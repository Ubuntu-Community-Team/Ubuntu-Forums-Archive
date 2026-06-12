---
title: "[SOLVED] java and opera browser"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by gandaran on 2008-01-28
I installed the opera browser and find it better than firefox, but I have problems with the plugins, especially the java plugin, I reinstalled sun java 6 and 5 several times and it never works, java doesn't show up!

heres the list

Plug-ins
Shockwave Flashapplication/futuresplash	spl
application/x-shockwave-flash	swf
/home/mfp/.opera/plugins/libflashplayer.so

NS4PluginProxyapplication/x-opera-nsplugin	-
/usr/lib/opera/plugins/libnpp.so

Windows Media Player Plug-in 10 (compatible; Totem)video/x-msvideo	avi
video/x-ms-asf	asf,asx
application/asx	-
video/x-ms-asf-plugin	-
application/x-mplayer2	-
video/x-ms-wm	wm
video/x-ms-wvx	wvx
video/x-ms-wmv	wmv
video/x-wmv	wmv
application/x-ms-wms	wms
/usr/lib/mozilla/plugins/libtotem-gmp-plugin.so

Totem Web Browser Plugin 2.20.0audio/wav	wav
audio/x-wav	wav
video/mpeg	mpeg,mpg,mpe,m2v,m1v,mpa
audio/mpeg	mp3,mp2,mpga
application/ogg	ogg
audio/ogg	ogg
audio/x-ogg	ogg
video/ogg	ogg
video/x-ogg	ogg
application/x-nsv-vp3-mp3	nsv
video/flv	flv
/usr/lib/mozilla/plugins/libtotem-basic-plugin.so

DivXÂ® Web Playervideo/divx	divx
/usr/lib/mozilla/plugins/libtotem-mully-plugin.so

QuickTime Plug-in 7.2.0video/mp4	mp4
video/quicktime	qt,mov
image/x-macpaint	pntg
image/x-quicktime	pict, pict1, pict2
video/x-m4v	m4v
/usr/lib/mozilla/plugins/libtotem-narrowspace-plugin.so

Adobe Reader 8.0application/pdf	pdf
application/vnd.adobe.xdp+xml	xdp
application/vnd.adobe.xfd+xml	xfd
application/vnd.fdf	fdf
application/vnd.adobe.xfdf	xfdf
/usr/lib/netscape/plugins-libc6/nppdf.so

how can make it work 
any ideas 
thanks

---

### Post by taurus on 2008-01-28
You did install the **sun-java6-plugin** package also, right?  Look in either /usr/lib/firefox/plugins or /usr/lib/mozilla/plugins to see if it shows up in there.  Otherwise, look in your ~/.mozilla/plugins if you have a plugins directory in ~/.mozilla.

---

### Post by gandaran on 2008-01-28
yes it shows up  and works perfertly on firefox, I have tried copying the mozilla path and paste on opera, but I must be doing something wrong or missing something else, I really need help here with the parths.
thanks

---

### Post by taurus on 2008-01-28
Do you see a java plugin in /usr/lib/opera/plugins?

```
ls -la /usr/lib/opera/plugins
```

---

### Post by gandaran on 2008-01-28
no and here's the result of  ls -la /usr/lib/opera/plugins

mfp@desktop:~$ ls -la /usr/lib/opera/plugins
total 208
drwxr-xr-x 2 root root  4096 2008-01-28 20:42 .
drwxr-xr-x 4 root root  4096 2008-01-28 09:44 ..
-rw-r--r-- 1 root root 96980 2008-01-04 22:15 libnpp.so
-rwxr-xr-x 1 root root  6960 2008-01-04 22:15 operaplugincleaner
-rwxr-xr-x 1 root root 89140 2008-01-04 22:15 operapluginwrapper
mfp@desktop:~$ 

this is the only folder where java is missing!

---

### Post by taurus on 2008-01-28
Can you post the outputs of both of these commands?

```
ls -la /usr/lib/firefox/plugins
ls -la /usr/lib/mozilla/plugins
```

---

### Post by gandaran on 2008-01-28
the problem is already solved
opera doesn't use the plugin, you just go to preferences»advanced»content»java options and look up the java path, in my case is «/usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/i386»

gandaran

---

