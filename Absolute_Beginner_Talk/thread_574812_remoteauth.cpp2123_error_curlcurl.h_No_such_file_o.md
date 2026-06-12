---
title: "remoteauth.cpp:21:23: error: curl/curl.h: No such file or directory"
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by hostyorkshire on 2007-10-13
Hi, I'm trying to install Movino Suite Server so I can stream from my Symbian N95 Phone.

I'm having a little trouble compiling it. I have curl installed but get this error.

Anyone any ideas?

root@andrew-desktop:/home/andrew/movino-suite-1.0/server# make
g++  -Wall -ggdb -I../core -DHAVE_THEORA  -c -o remoteauth.o remoteauth.cpp

remoteauth.cpp:21:23: error: curl/curl.h: No such file or directory
remoteauth.cpp: In static member function ‘static void RemoteAuth::init()’:
remoteauth.cpp:26: error: ‘CURL_GLOBAL_ALL’ was not declared in this scope
remoteauth.cpp:26: error: ‘curl_global_init’ was not declared in this scope
remoteauth.cpp: In static member function ‘static void RemoteAuth::finish()’:
remoteauth.cpp:30: error: ‘curl_global_cleanup’ was not declared in this scope
remoteauth.cpp: In static member function ‘static bool RemoteAuth::authenticate(void*, const char*, const uint8_t*, int, const uint8_t*)’:
remoteauth.cpp:54: error: ‘CURL’ was not declared in this scope
remoteauth.cpp:54: error: ‘curl’ was not declared in this scope
remoteauth.cpp:54: error: ‘curl_easy_init’ was not declared in this scope
remoteauth.cpp:55: error: ‘CURLOPT_URL’ was not declared in this scope
remoteauth.cpp:55: error: ‘curl_easy_setopt’ was not declared in this scope
remoteauth.cpp:56: error: ‘CURLOPT_NOPROGRESS’ was not declared in this scope
remoteauth.cpp:57: error: ‘CURLOPT_NOSIGNAL’ was not declared in this scope
remoteauth.cpp:58: error: ‘CURLOPT_TIMEOUT’ was not declared in this scope
remoteauth.cpp:59: error: ‘CURLOPT_WRITEFUNCTION’ was not declared in this scope
remoteauth.cpp:60: error: ‘CURLOPT_WRITEDATA’ was not declared in this scope
remoteauth.cpp:67: error: ‘sprintf’ was not declared in this scope
remoteauth.cpp:72: error: ‘sprintf’ was not declared in this scope
remoteauth.cpp:89: error: ‘curl_escape’ was not declared in this scope
remoteauth.cpp:91: error: ‘curl_free’ was not declared in this scope
remoteauth.cpp:94: error: ‘CURLOPT_POSTFIELDS’ was not declared in this scope
remoteauth.cpp:97: error: ‘CURLcode’ was not declared in this scope
remoteauth.cpp:97: error: expected `;' before ‘code’
remoteauth.cpp:100: error: ‘CURLINFO_RESPONSE_CODE’ was not declared in this scope
remoteauth.cpp:100: error: ‘curl_easy_getinfo’ was not declared in this scope
remoteauth.cpp:101: error: ‘curl_easy_cleanup’ was not declared in this scope
remoteauth.cpp:102: error: ‘code’ was not declared in this scope
remoteauth.cpp:103: error: ‘stderr’ was not declared in this scope
remoteauth.cpp:103: error: ‘curl_easy_strerror’ was not declared in this scope
remoteauth.cpp:103: error: ‘fprintf’ was not declared in this scope
make: *** [remoteauth.o] Error 1
root@andrew-desktop:/home/andrew/movino-suite-1.0/server# 

Thanks

Andrew

---

### Post by milosz.galazka on 2007-10-13
for example:
```
apt-get install libcurl4-openssl-dev
```
or 
```
apt-get install libcurl4-gnutls-dev
```

---

### Post by hostyorkshire on 2007-10-14
Thanks, it's worked!

I now have my Nokia N95 streaming video to my ubuntu box via LAN or 3G.
Excellent..

---

### Post by oldman on 2007-10-14
Is it possible to ask you what kind of setting you are using. Everything goes fine until I start to watch on the PC. I have tried jpeg,mpeg and raw in the setting but all I get is a black window and nothing gets stored on the server.

Thank you!

---

### Post by hostyorkshire on 2007-10-14
Hi I'm using the symbian 3 version of Movino and not the java version.

I set my sound as PCM and the video JPEG. The image quality slider is half way.

I can stream via LAN or 3G and it ends up in the movino server folder as an  .ogg file which I can play in totem.

I have tried getting the live stream to the web using the standalone and the drupal module but yet with no success. I think the problem maybe the router but I'm going to check all settings again.

Hope this helps.

---

### Post by oldman on 2007-10-15
Hi !

Thank you ! Now it is working. It saves in ogg files. I could not watch the stream with mplayer, but with Totem I could watch it live. The live version lags more than 5 sec behind and jumps. But it was impressiv. I shall twist a little more and also try it on outside my lan. 

Regards!

---

### Post by hostyorkshire on 2007-10-15
hehe...good stuff!

Let me know if you can get it streaming live on the web using the standalone app or using drupal. Don't have time now until the weekend to play.

Cheers!

---

