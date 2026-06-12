---
title: "Arabic Encoding , PLEASE HELP !!! PLEASE!!!!!"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by Nadeem97 on 2007-06-26
Hello ,

I really solved nearly all of my problems, but still this problem not solved...

i cant get this encoding in order to view arabic words correctly ...so VLC shows missed up subtitles ... and so does amsn , also Gedit , and Thunderbird ,,, and all other programs..

ive installed the arabic support packages + fonts , also , ive tried cp1256 and the iso-8859-6 encodings which are available in ubuntu , but no luck...

Please , HELP GUYS !!!! i really dont want to get back to windows !!! thanks....

---

### Post by jmfa59 on 2007-06-26
How about writing in arabic is it bad too
Do you have the problem in the office doc. or in browser.

---

### Post by Nadeem97 on 2007-06-26
i can write in arabic with no problems , i can also see arabic in Firefox , but Amsn , VLC , and any other program shows incorrect form of characters....

---

### Post by Nadeem97 on 2007-06-27
no one ?

---

### Post by Inxsible on 2007-06-27
Hey Nadeem,
 
Could you tell me what packages you installed to have Firefox read Arabic script clearly?
 
I assume, the Arabic script will be ok to use in Urdu newspapers too. Also would you know the packages to read Hindi / Devnagari script clearly in Firefox?

---

### Post by Nadeem97 on 2007-06-27
Hello ,

Well , Actually FireFox could read arabic with no problems without the "packages" were installed , and about the packages , i havent installed them manually, i went to Langauges settings from the preferences tab , and selected arabic support , it downloaded and installed 8 packages .. but that had no change at all with AMSN and/or VLC .... i think if there is " Windows-1256 encoding " then the problem would be solved , isnt it  ?

---

### Post by Nadeem97 on 2007-06-27
i really need some help guys ,

---

### Post by p_quarles on 2007-06-27
I just did a search in Synaptic for "arabic," and quite a few packages came up. You might do the same, and see if there are any that weren't downloaded when you changed the language setting. 

You might also go to VLC's site and see if they have any plugins there.

---

### Post by zanjabeel5 on 2007-08-01
To view Arabic (and other exotic) Codings in Gedit I do the following:

from Gedit menu 
file ->  open

select your file and from the character coding **drop down menu** select add/remove
there you can add arabic-windows and few more other encodings.
this way I was able to see Arabic text in gedit

good luck.

---

### Post by capink on 2007-08-01
I was able to solve the problem of arabic subtitles in vlc and mplayer by installing libfirbidi2. It is not in the repositories so I attached here. 

Beware that for subtitles to be showed they must be utf8. So you must convert any subtitles encoded in other charsets to utf8. Also don't forget to select utf8 as default character set in vlc and mplayer.

---

### Post by ah4uahmed on 2007-08-27
thankssssssssssssssssssssssssssss

---

### Post by capink on 2007-08-27
Welcome to Ubuntu.

---

### Post by yousefla on 2007-12-27
Hi Capink

How can I install your .bed file to my Windows version of VLC to be able to play the Arabic subtitles?

Thanks in advance!

---

### Post by KhaaL on 2007-12-27
the **.deb** file is installed to the system i belive, you only need to install VLC through the repository in order for it to work. 

I don't think it's gonna to work with a windows version (this is a linux forum just in case you've missed!).

:) &#1582;&#1575;&#1604;&#1583; --

---

### Post by capink on 2007-12-27
As the previous poster metioned it cannot be installed on windows. But maybe another solution for windows exist.

---

### Post by gohamad on 2008-05-22
Dear capink
where shold I put your attach file?

I am facing also same problem.

---

### Post by capink on 2008-05-22
You have to install it by double clicking it. You can ALSO do it from the terminal:

```
sudo dpkg -i libfribidi0_0.20-1_i386.deb
```

---

