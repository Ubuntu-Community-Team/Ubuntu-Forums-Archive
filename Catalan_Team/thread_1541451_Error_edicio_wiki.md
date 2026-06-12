---
title: "Error edicio wiki"
date: 2010-07-29
forum: Catalan Team
---

### Post by abosch on 2010-07-29
Volia editar al wiki d'ubuntu (a la Viquipèdia no tinc problema) i m'envia error. Després de googlejar, no acabo de treure'n l'entrellat. Desconec si havia d'instal·lar el paquet 
```
phyton-moinmoin
```
tanmateix després de fer-ho tampoc ha millorat.

Enganxo a veure si em podeu donar un cop de mà. Cercant info pel wiki del LocoCat, arribat a una plana on recomanava editar per anar veient el que s'explicava i tampoc m'ha permès (Internal Server Error)


```
UnicodeEncodeError

'ascii' codec can't encode character u'\xf2' in position 69: ordinal not in range(128)

If you want to report a bug, please save this page and attach it to your bug report.

    * Show debugging information
    * Report bug
    * Visit MoinMoin wiki

Traceback

A problem occurred in a Python script. Here is the sequence of function calls leading up to the error, in the order they occurred.

   1.

      /var/lib/python-support/python2.5/MoinMoin/request/request_fcgi.py in __init__ (self=<MoinMoin.request.request_fcgi.Request object at 0x1dc0690>, fcgRequest=<MoinMoin.support.thfcgi.Request instance at 0x60425f0>, env={'DOCUMENT_ROOT': '/srv/wiki.ubuntu.com/www/', 'GATEWAY_INTERFACE': 'CGI/1.1', 'HTTP_ACCEPT': 'text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8', 'HTTP_ACCEPT_CHARSET': 'ISO-8859-1,utf-8;q=0.7,*;q=0.7', 'HTTP_ACCEPT_ENCODING': 'gzip,deflate', 'HTTP_ACCEPT_LANGUAGE': 'ca,en-us;q=0.7,en;q=0.3', 'HTTP_CACHE_CONTROL': 'max-age=259200', 'HTTP_CONNECTION': 'keep-alive', 'HTTP_COOKIE': '__utma=230736537.1641853331.1254159010.128039537...jqbwhrsv39df9cuhpwisdtnhervef05; __utmc=230736537', 'HTTP_HOST': 'wiki.ubuntu.com', ...}, form=FieldStorage(None, None, [MiniFieldStorage('acti...ieldStorage('openid.sreg.nickname', 'abosch-b')]), properties={})
         1. 26 self.fcgform = form
         2. 27 self._setup_vars_from_std_env(env)
         3. 28 RequestBase.__init__(self, properties)
         4. 29
         5. 30 except Exception, err:
          * global RequestBase = <class 'MoinMoin.request.RequestBase'>
          * RequestBase.__init__ = <unbound method RequestBase.__init__>
          * self = <MoinMoin.request.request_fcgi.Request object at 0x1dc0690>
          * properties = {}
   2.

      /var/lib/python-support/python2.5/MoinMoin/request/__init__.py in __init__ (self=<MoinMoin.request.request_fcgi.Request object at 0x1dc0690>, properties={})
         1. 205 # set self.user even if _handle_auth_form raises an Exception
         2. 206 self.user = None
         3. 207 self.user = self._handle_auth_form(user_obj)
         4. 208 del user_obj
         5. 209 self.cfg.session_handler.after_auth(self, self.cfg.session_id_handler, self.user)
          * self = <MoinMoin.request.request_fcgi.Request object at 0x1dc0690>
          * self.user = None
          * self._handle_auth_form = <bound method Request._handle_auth_form of <Moin...equest.request_fcgi.Request object at 0x1dc0690>>
          * user_obj = None
   3.

      /var/lib/python-support/python2.5/MoinMoin/request/__init__.py in _handle_auth_form (self=<MoinMoin.request.request_fcgi.Request object at 0x1dc0690>, user_obj=None)
         1. 610 return self.handle_auth(user_obj, attended=True, username=username,
         2. 611 password=password, login=login, logout=logout,
         3. 612 stage=stage, openid_identifier=oid)
         4. 613
         5. 614 def handle_auth(self, user_obj, attended=False, **kw):
          * stage = u'openid'
          * openid_identifier undefined
          * oid = None
   4.

      /var/lib/python-support/python2.5/MoinMoin/request/__init__.py in handle_auth (self=<MoinMoin.request.request_fcgi.Request object at 0x1dc0690>, user_obj=<MoinMoin.user.User at 0x6042a28 name:u'abosch-b' valid:1>, attended=True, **kw={'login': True, 'logout': False, 'openid_identifier': None, 'password': None, 'stage': u'openid', 'username': None})
         1. 658 url = url.replace('%return', quote(nextstage))
         2. 659 self._auth_redirected = True
         3. 660 self.http_redirect(url)
         4. 661 return user_obj
         5. 662 msg = ret.message
          * self = <MoinMoin.request.request_fcgi.Request object at 0x1dc0690>
          * self.http_redirect = <bound method Request.http_redirect of <MoinMoin.request.request_fcgi.Request object at 0x1dc0690>>
          * url = u'/CatalanTeam/Parides/AvatarsMensualsF\xf2rum/072010/'
   5.

      /var/lib/python-support/python2.5/MoinMoin/request/__init__.py in http_redirect (self=<MoinMoin.request.request_fcgi.Request object at 0x1dc0690>, url=u'http://wiki.ubuntu.com/CatalanTeam/Parides/AvatarsMensualsF\xf2rum/072010/')
         1. 1289 """
         2. 1290 url = self.getQualifiedURL(url)
         3. 1291 self.emit_http_headers(["Status: 302 Found", "Location: %s" % url])
         4. 1292
         5. 1293 def emit_http_headers(self, more_headers=[], testing=False):
          * self = <MoinMoin.request.request_fcgi.Request object at 0x1dc0690>
          * self.emit_http_headers = <bound method Request.emit_http_headers of <Moin...equest.request_fcgi.Request object at 0x1dc0690>>
          * url = u'http://wiki.ubuntu.com/CatalanTeam/Parides/AvatarsMensualsF\xf2rum/072010/'
   6.

      /var/lib/python-support/python2.5/MoinMoin/request/__init__.py in emit_http_headers (self=<MoinMoin.request.request_fcgi.Request object at 0x1dc0690>, more_headers=['Status: 302 Found', u'Location: http://wiki.ubuntu.com/CatalanTeam/Parides/AvatarsMensualsF\xf2rum/072010/'], testing=False)
         1. 1324 for header, trace in all_headers:
         2. 1325 if isinstance(header, unicode):
         3. 1326 header = header.encode('ascii')
         4. 1327 key, value = header.split(':', 1)
         5. 1328 lkey = key.lower()
          * header = u'Location: http://wiki.ubuntu.com/CatalanTeam/Parides/AvatarsMensualsF\xf2rum/072010/'
          * header.encode = <built-in method encode of unicode object at 0x1a53b40>

UnicodeEncodeError

'ascii' codec can't encode character u'\xf2' in position 69: ordinal not in range(128)

    * args = ('ascii', u'Location: http://wiki.ubuntu.com/CatalanTeam/Parides/AvatarsMensualsF\xf2rum/072010/', 69, 70, 'ordinal not in range(128)')
    * encoding = 'ascii'
    * end = 70
    * message = ''
    * object = u'Location: http://wiki.ubuntu.com/CatalanTeam/Parides/AvatarsMensualsF\xf2rum/072010/'
    * reason = 'ordinal not in range(128)'
    * start = 69

System Details

    * Date: Thu, 29 Jul 2010 09:51:55 +0000
    * Platform: Linux jostaberry 2.6.24-27-server #1 SMP Fri Mar 12 01:23:09 UTC 2010 x86_64
    * Python: Python 2.5.2 (/usr/bin/python)
    * MoinMoin: Release 1.6.3 (release)


```

Ressaltant les línies 28, 207, 612,660, 1291, 1326

---

### Post by papapep on 2010-07-29
No, no, ni molt menys. No cal instal·lar absolutament res per a emprar el wiki. Només cal un navegador normal i corrent: Firefox, Chrome, Opera, l'innombrable...
Deus tenir algun problema al navegador, has provat amb algun altre?

---

### Post by abosch on 2010-07-31
Acabo d'instal·lar el Chromium i tampoc no puc editar al wiki.  :(

---

### Post by papapep on 2010-07-31
Això és un Expedient X, Alexandre...

Passa'm quina pàgina en concret és aquesta que et diu que has d'editar per veure bé, a veure si em passa el mateix.

---

### Post by abosch on 2010-07-31
La plana informativa on em donava l'error "Internal Server Error" és,

[HTML]https://wiki.ubuntu.com/CatalanTeam/Recursos/ComEditarElWiki[/HTML]


A aquesta si que puc fer el login/register i editar. Però el missatge d'error em contínua per afegir plana pels AvatarsMensualsFòrum on després de fer el login/register em salta el "UnicodeEncodeError" que penjava l'altre dia.

Gràcies

---

### Post by papapep on 2010-07-31
Prova ara que [l'he creat]("https://wiki.ubuntu.com/CatalanTeam/Parides/AvatarsMensualsF%C3%B2rum/072010") buida, a veure si et deixa.

---

### Post by abosch on 2010-07-31
No, em continua donant el mateix error ...

Era per afegir taula i avatars juliol, no té més importància.

---

