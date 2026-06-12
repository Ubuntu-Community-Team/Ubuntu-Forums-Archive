---
title: "Descarregar llibres de Google Books"
date: 2018-02-01
forum: Catalan Team
---

### Post by jinglada on 2018-02-01
Hola companys: Vaig trobar aquest programa [https://github.com/pysheng/pysheng](https://github.com/pysheng/pysheng) i el vaig instal·lar segons indica. He provat l'execució directa i la GUI i no hi ha manera que funcioni. Us copio a sota el que em dóna. Gràcies a la bestreta per la vostra ajuda, Joan

joan@joan-Aspire-E1-572:~/pysheng-0.1/pysheng$ pysheng usMhO9zsFKoC
Traceback (most recent call last):
  File "/usr/local/bin/pysheng", line 6, in <module>
    sys.exit(pysheng.main(sys.argv[1:]))
  File "/usr/local/lib/python2.7/dist-packages/pysheng/download.py", line 119, in main
    for info, page, image_data in download_book(url):
  File "/usr/local/lib/python2.7/dist-packages/pysheng/download.py", line 104, in download_book
    image_data = download(image_url, opener=opener)
  File "/usr/local/lib/python2.7/dist-packages/pysheng/download.py", line 90, in download
    return lib.download(*args, **dict(kwargs, agent=AGENT))
  File "/usr/local/lib/python2.7/dist-packages/pysheng/lib.py", line 56, in download
    return opener.open(request).read()
  File "/usr/lib/python2.7/urllib2.py", line 435, in open
    response = meth(req, response)
  File "/usr/lib/python2.7/urllib2.py", line 548, in http_response
    'http', request, response, code, msg, hdrs)
  File "/usr/lib/python2.7/urllib2.py", line 473, in error
    return self._call_chain(*args)
  File "/usr/lib/python2.7/urllib2.py", line 407, in _call_chain
    result = func(*args)
  File "/usr/lib/python2.7/urllib2.py", line 556, in http_error_default
    raise HTTPError(req.get_full_url(), code, msg, hdrs, fp)
urllib2.HTTPError: HTTP Error 404: Not Found

------------
versió GUI
------------

joan@joan-Aspire-E1-572:~/pysheng-0.1/pysheng$ pysheng-gui
Traceback (most recent call last):
  File "/usr/local/lib/python2.7/dist-packages/pysheng/gui.py", line 163, in download_book
    elapsed_cb=functools.partial(on_elapsed, widgets, "image"))
HTTPError: HTTP Error 404: Not Found
Exception in thread Thread-4:
Traceback (most recent call last):
  File "/usr/lib/python2.7/threading.py", line 801, in __bootstrap_inner
    self.run()
  File "/usr/lib/python2.7/threading.py", line 754, in run
    self.__target(*self.__args, **self.__kwargs)
  File "/usr/local/lib/python2.7/dist-packages/pysheng/asyncjobs.py", line 358, in _thread_manager
    request, size = connect_opener(url, opener, headers)
  File "/usr/local/lib/python2.7/dist-packages/pysheng/asyncjobs.py", line 275, in connect_opener
    response = opener.open(request)
  File "/usr/lib/python2.7/urllib2.py", line 435, in open
    response = meth(req, response)
  File "/usr/lib/python2.7/urllib2.py", line 548, in http_response
    'http', request, response, code, msg, hdrs)
  File "/usr/lib/python2.7/urllib2.py", line 473, in error
    return self._call_chain(*args)
  File "/usr/lib/python2.7/urllib2.py", line 407, in _call_chain
    result = func(*args)
  File "/usr/lib/python2.7/urllib2.py", line 556, in http_error_default
    raise HTTPError(req.get_full_url(), code, msg, hdrs, fp)
HTTPError: HTTP Error 404: Not Found

------------------------------------------
potser el tinc mal instal·lat?
------------------------------------------

joan@joan-Aspire-E1-572:~/pysheng-0.1$ ls -al
total 44
drwxr-xr-x   7 joan joan  4096 gen 25 18:14 .
drwxr-xr-x 113 joan joan 12288 gen 26 09:54 ..
drwxr-xr-x   2 joan joan  4096 mar 22  2010 bin
drwxr-xr-x   4 root root  4096 gen 25 18:14 build
-rw-r--r--   1 joan joan   130 mar 22  2010 CHANGELOG
drwxr-xr-x   2 joan joan  4096 mar 22  2010 data
drwxr-xr-x   2 joan joan  4096 mar 22  2010 pysheng
-rw-r--r--   1 joan joan  1207 mar 22  2010 setup.py
drwxr-xr-x   3 joan joan  4096 mar 22  2010 test

---

### Post by wgarcia on 2018-02-04
Com el vas instal·lar? He provat (com posa al repositori):

```
wget http://pysheng.googlecode.com/files/pysheng-VERSION.tgz
```

i em diu que no troba aquest fitxer.

---

### Post by jinglada on 2018-02-04
> **wgarcia said:**
> Com el vas instal·lar? He provat (com posa al repositori):

```
wget http://pysheng.googlecode.com/files/pysheng-VERSION.tgz
```

i em diu que no troba aquest fitxer.

Em vaig guiar pel que diu a [https://paulodev.com.br/en/blog/linux/37-download-google-book-in-linux](https://paulodev.com.br/en/blog/linux/37-download-google-book-in-linux) i vaig trovar que  [https://code.google.com/archive/p/pysheng/downloads](https://code.google.com/archive/p/pysheng/downloads), la versió és pysheng-0.1.tgz. 
Llavors vaig fer wget [https://code.google.com/archive/p/pysheng/pysheng-0.1.tgz](https://code.google.com/archive/p/pysheng/pysheng-0.1.tgz)

---

### Post by wgarcia on 2018-02-05
Lògic, VERSION = 0.1.

Bé, ho he instal·lat i em dóna el mateix error que tu. Em sembla que hi ha problemes a la programació per interpretar les adreces dels llibres.

---

### Post by jinglada on 2018-02-05
> **wgarcia said:**
> Lògic, VERSION = 0.1.

Bé, ho he instal·lat i em dóna el mateix error que tu. Em sembla que hi ha problemes a la programació per interpretar les adreces dels llibres.

L'usuari T.Collons d'ubuntu-cat@lists.ubuntu.com m'ha dit:

> A mi " pysheng usMhO9zsFKoC" em descarrega un llibre en png, però si intento executar el gui, en dona aquest error:

**ImportError: No module named glade**

---

