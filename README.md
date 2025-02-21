# news-reader
Reader de Noticias


- La idea es que notebook LM los lea y genere un podcast con el resumen.
- Puedo hacer uno por día.
- incluso te permite interactar con ellos, ver que pasa cuando descargo la interacción.


El async hace que notebook lM no vea toda la noticia, tal vez almacenar en DB las noticias, y mostrarlas con PHP. Las URL de feed podrían tener id, y así evitar si algun script corta los query params. 

http://misitio.com/1/25/23/22/43/noticias.php


esta la web en githubpages... https://tomichgit.github.io/news-reader/
uso un proxy para cors, 


```js
// Alternative proxies - try these if the first one doesn't work
const corsProxies = {
    allOrigins: 'https://api.allorigins.win/raw?url=',
    corsproxy: 'https://corsproxy.io/?',
    corsAnywhere: 'https://cors-anywhere.herokuapp.com/'
};
```

pero se recomienda crear mi propio proxy en mi server PHP...


```php
<?php
header('Access-Control-Allow-Origin: *');
header('Content-Type: application/xml');

$url = $_GET['url'];
if (filter_var($url, FILTER_VALIDATE_URL)) {
    echo file_get_contents($url);
} else {
    http_response_code(400);
    echo 'Invalid URL';
}

```

```js	
const proxyUrl = `proxy.php?url=${encodeURIComponent(url)}`;
const response = await fetch(proxyUrl);
```	

        proyecto: https://github.com/tomichGIT/news-reader
        <br>
        Links de feeds:
        https://www.clarin.com/rss.html?srsltid=AfmBOor7TAwA_ORqTSkrPO_PPbYoo7mWl6OBsQs_wJOCWHcELWi30nkr
        https://www.reddit.com/r/argentina/.rss