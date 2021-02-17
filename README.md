# postfix-utils

## Introdução

Este repositório criei para colocar dicas para uso do MTA postfix.

## Tradução do arquivo bounce.cf para o português brasil

O comando para verificar se o arquivo `bounce.cf` está correto está abaixo:

```bash
# postconf -b /etc/postfix/bounce.cf
```

Caso ocorra um erro do tipo

```
postfix/bounce: warning: /etc/postfix/bounce.cf: 8-bit message text in failure template
postfix/bounce: warning: please specify a charset value other than us-ascii
postfix/bounce: warning: -- ignoring this template for now
postfix/bounce: warning: /etc/postfix/bounce.cf: 8-bit message text in delay template
postfix/bounce: warning: please specify a charset value other than us-ascii
postfix/bounce: warning: -- ignoring this template for now
postfix/bounce: warning: /etc/postfix/bounce.cf: non-ASCII "Subject" header value in success template -- ignoring this template
postfix/bounce: warning: /etc/postfix/bounce.cf: non-ASCII "Subject" header value in verify template -- ignoring this template
```

Converta o arquivo bounce.cf para ascii com o util iconv:

```bash
# cd /etc/postfix/
# cat bounce.cf | iconv -f utf-8 -t ascii//TRANSLIT > bounce2.cf
# mv bounce2.cf bounce.cf
```
