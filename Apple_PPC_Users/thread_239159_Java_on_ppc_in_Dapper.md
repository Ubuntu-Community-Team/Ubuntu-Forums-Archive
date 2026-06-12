---
title: "Java on ppc in Dapper"
date: 2006-08-18
forum: Apple PPC Users
---

### Post by zeker on 2006-08-18
Ok. 

I am runnning an iBook G4 and kubuntu 6.06 

I have followed the instructions here for installing java on ppc

[https://help.ubuntu.com/community/Java#head-0948e66f605ec3c2af4f264c5cfc56f4175659eb](https://help.ubuntu.com/community/Java#head-0948e66f605ec3c2af4f264c5cfc56f4175659eb)

and I went through all the discussion forums and posts here looking for a fix. (there was another thread in dapper development but it is closed)

My java works, I can run othr java programs. 

Firefox chrashs and shuts down whenever it encounters a java site. 

I am currently working around this by not linking from the /plugins folder to the firefoxplugin.so but this does not help me use java sites

any thoughts on this one or links that I missed?

---

### Post by avtolle on 2006-08-18
Did you install the JDK for 1.5, or 1.4; only the 1.5 will work with the Firefox plugin. By the Way, IBM calls 1.5 5.0. I have installed Java w/the Firefox plugin by following the link you have in your post, downloading the file for 1.5 JDK, then following the workaround at the end of the page, which is mandatory for the plug in to work. I hope this makes sense to you. Good luck.

---

### Post by zeker on 2006-08-21
thanks for the response. 

I downloaded the j2sdk1.5 from the IBM developerworks site. I converted it to a .deb package and installed it using kpackage. I then created a symbolic link from by /mozilla/plugins directory to the libjavaplugin_oji.so in the java 1.5 directory. 

What am I missing?

---

### Post by avtolle on 2006-08-21
I'm not sure what the issue is, but the following is my sym link:

```
 ln -s /usr/lib/j2sdk1.5-ibm/jre/bin/libjavaplugin_oji.so /usr/lib/mozilla-firefox/plugins 
```

Also, did you do: ```
 sudo update-alternatives --config java 
``` and select the correct one?

I had issues until I did both. HTH.

---

### Post by gnumac on 2006-08-26
For all of you running powerpc64 (Macintosh G5) use the   ibm-java2-sdk-50-linux-ppc.tgz and not the  ibm-java2-sdk-50-linux-ppc64.tgz version as it make-jpkg wiill not work 
See [http://lists.alioth.debian.org/pipermail/pkg-java-maintainers/2006-April/008007.html]("http://lists.alioth.debian.org/pipermail/pkg-java-maintainers/2006-April/008007.html") for more info.

---

### Post by zeker on 2006-08-28
Avatole:

If I run ```
"sudo update-alternatives --config java"
```

I get the following:

```


There are 3 alternatives which provide 'java'.

  Selection     Alternative
-----------------------------------------------------
 +    1         /usr/li/j2re1.5-ibm/jre/bin/java
*     2         /usr/lib/j2dsk1.5-ibm/bin/java         
      3         /usr/lib/jdsdk1.4-ibm/bin/java

Press enter to keep the default [*]. or type selection number:


```

I then make the exact link you were talking about

```
 
 ln -s /usr/lib/j2sdk1.5-ibm/jre/bin/libjavaplugin_oji.so /usr/lib/mozilla-firefox/plugins 

```

Only I didn't have permission to that folder so I changed the permisions (unless I was supposed to use sudo?) 

Got the link to work. 

Still no go.

---

### Post by jpowermacg5 on 2006-08-28
Speaking of java on PPC mac... I've only got it to work with programs... never worked with firefox... unlike those instructions above, which i did wrong the first time... I used the jre package rather then the SDK... since it would seem more like i needed the jre package rather then source code. Anyways... after the update alternatives it works with java based programs like frostwire... though i symlinked about 6 locations for firefox plugin.. and never got it to work... didn't try /usr/lib/mozilla-firefox/plugins i don't think though.... guess i'll give that a shot also.

---

### Post by gnumac on 2006-08-29
> **jpowermacg5 said:**
>  didn't try /usr/lib/mozilla-firefox/plugins i don't think though.... guess i'll give that a shot also.

Do so. Worked fine for me with the SDK

---

