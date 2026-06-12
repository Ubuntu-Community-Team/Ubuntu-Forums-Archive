---
title: "Problemes instal·lant idcat certificat digital"
date: 2019-11-12
forum: Catalan Team
---

### Post by martamarta on 2019-11-12
Hola!

Estic provant d'instal·lar el certificat digital idCAT i no me n'acabo d'ensortir. 

Estic seguint els passos descrits a[ https://www.idcat.cat/idcat/jsp/guies/clauer/linux/guia%20usuari%20clauer%20idCAT-Linux.pdf]("https://www.idcat.cat/idcat/jsp/guies/clauer/linux/guia%20usuari%20clauer%20idCAT-Linux.pdf") i em quedo al pas "make".

Més especificament, de moment he fet el següent: 

1. M'he baixat el programari des de [www.idcat.cat/clauer]("http://www.idcat.cat/clauer").

2. Seguint les instruccions, he entrat a la carpeta ClauerLinux-3.0.8, he instal·lat alguns paquets necessaris i he fet córrer ./configure. És a dir:
```


cd ClauerLinux-3.0.8/

# Install dependencies
sudo apt install g++ libnss3-dev libssl-dev gawk

# Run configure
./configure --enable-64

```

3. El problema bé quan faig ```
 make 
```

Em surten els següents errors:

```

CRYPTOWrap.c:251:18: **error:** storage size of 'ctx' isn't known
  251 |   EVP_CIPHER_CTX **ctx**;
      |                  **^~~**
CRYPTOWrap.c: In function 'CRYPTO_PBE_Cifrar':
CRYPTOWrap.c:376:18: **error:** storage size of 'ctx' isn't known
  376 |   EVP_CIPHER_CTX **ctx**;
      |                  **^~~**
CRYPTOWrap.c: In function 'CRYPTO_Random':
CRYPTOWrap.c:476:3: warning: 'RAND_pseudo_bytes' is deprecated [-Wdeprecated-declarations]
  476 |   if ( ! RAND_pseudo_bytes(bufferRandom, bytes) )
      |   ^~
In file included from /usr/include/openssl/evp.h:13,
                 from CRYPTOWrap.c:52:
/usr/include/openssl/rand.h:44:1: note: declared here
   44 | DEPRECATEDIN_1_1_0(int RAND_pseudo_bytes(unsigned char *buf, int num))
      | ^~~~~~~~~~~~~~~~~~
CRYPTOWrap.c: In function 'CRYPTO_GenerarParLlaves':
CRYPTOWrap.c:637:3: warning: 'RSA_generate_key' is deprecated [-Wdeprecated-declarations]
  637 |   rsaLlave = RSA_generate_key(bits, 3, NULL, NULL);
      |   ^~~~~~~~
In file included from /usr/include/openssl/evp.h:13,
                 from CRYPTOWrap.c:52:
/usr/include/openssl/rsa.h:234:1: note: declared here
  234 | DEPRECATEDIN_0_9_8(RSA *RSA_generate_key(int bits, unsigned long e, void
      | ^~~~~~~~~~~~~~~~~~
CRYPTOWrap.c: In function 'CRYPTO_Cifrar':
CRYPTOWrap.c:1312:18: **error:** storage size of 'ctx' isn't known
 1312 |   EVP_CIPHER_CTX **ctx**;
      |                  **^~~**
CRYPTOWrap.c: In function 'CRYPTO_Descifrar':
CRYPTOWrap.c:1401:18: **error:** storage size of 'ctx' isn't known
 1401 |   EVP_CIPHER_CTX **ctx**;
      |                  **^~~**
CRYPTOWrap.c: In function 'CRYPTO_EVPPKEY_Id':
CRYPTOWrap.c:1616:14: **error:** storage size of 'mdCtx' isn't known
 1616 |   EVP_MD_CTX **mdCtx**;
      |              **^~~~~**
In file included from /usr/include/openssl/asn1.h:23,
                 from /usr/include/openssl/objects.h:15,
                 from /usr/include/openssl/evp.h:28,
                 from CRYPTOWrap.c:52:
CRYPTOWrap.c:1618:26: **error:** dereferencing pointer to incomplete type 'EVP_PKEY' {aka 'struct evp_pkey_st'}
 1618 |   tamE = BN_num_bytes(evp**->**pkey.rsa->e);
      |                          **^~**
CRYPTOWrap.c:1649:5: warning: implicit declaration of function 'EVP_MD_CTX_cleanup'; did you mean 'EVP_MD_CTX_create'? [-Wimplicit-function-declaration]
 1649 |     EVP_MD_CTX_cleanup(&mdCtx);
      |     ^~~~~~~~~~~~~~~~~~
      |     EVP_MD_CTX_create
CRYPTOWrap.c: In function 'CRYPTO_BLOB2LLAVE':
CRYPTOWrap.c:3332:7: **error:** dereferencing pointer to incomplete type 'RSA' {aka 'struct rsa_st'}
 3332 |   pKey**->**n = BN_bin2bn(auxBlob+sizeof(BLOBHEADER)+sizeof(RSAPUBKEY), rsaPubKey->bitlen/8, NULL);
      |       ^~

```

A algú més li ha passat? No sé si és que em falta instal·lar algun altre paquet, o que hi ha algun pas que no faig... em podríeu donar un cop de mà? Estaré molt agraïda!!

Moltes gràcies d'avançada! (I perdoneu si la pregunta és molt trivial!!)

Salut,

Marta

---

