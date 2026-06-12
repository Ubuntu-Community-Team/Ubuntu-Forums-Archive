---
title: "what ppd file?"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by mills on 2007-04-30
decided to get rid of windows and try a different flavour of linux in its place but i need to sort out printing in ubuntu 1st (only reason i still have windows is for printing)

so simple question when i open printing in administartion menu and try to install the driver its telling me to select a ppd file, but i cant find a ppd file anywhere, any ideas?

---

### Post by Najand on 2007-04-30
What printer model are you using and what is its manufactor?

---

### Post by mills on 2007-04-30
sorry, its a lexmark x1180

its being recognized and i it has a few jobs waiting but nothing is happening so iam guessing its because i cant find a ppd file to install the driver

and iam trying the 1100 driver cuase its  the closest number to 1180

---

### Post by mills on 2007-04-30
ok just realised i gotta do all this, forget about it, rather keep windows

[http://ubuntuforums.org/showthread.php?t=49714&highlight=X1150](http://ubuntuforums.org/showthread.php?t=49714&highlight=X1150).

---

### Post by klytu on 2007-04-30
> **mills said:**
> decided to get rid of windows and try a different flavour of linux in its place but i need to sort out printing in ubuntu 1st (only reason i still have windows is for printing)

so simple question when i open printing in administartion menu and try to install the driver its telling me to select a ppd file, but i cant find a ppd file anywhere, any ideas?

Your specific printer model is not listed in the database at [COLOR="Red"]**_[[COLOR="Red"][B][U]www.linuxprinting.org_**[/COLOR]]("http://www.linuxprinting.org")[/U][/B][/COLOR], but a couple of other models in the Lexmark X11xx series work well with the CUPS z600 driver. Also, [COLOR="Red"]**_[[COLOR="Red"][B][U]check out this thread_**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=49714&highlight=X1150.")[/U][/B][/COLOR]. It's a couple of years old, but it might help.

---

### Post by mills on 2007-04-30
this why i couldnt be bothered, i have the driver in a folder on the desktop

```
alex@alex-desktop:~$ mv CJLZ600LE-CUPS-1.0-1.TAR.gz lexmark
mv: cannot stat `CJLZ600LE-CUPS-1.0-1.TAR.gz': No such file or directory

alex@alex-desktop:~$ cd Desktop

alex@alex-desktop:~/Desktop$ mv CJLZ600LE-CUPS-1.0-1.TAR.gz lexmark
mv: cannot stat `CJLZ600LE-CUPS-1.0-1.TAR.gz': No such file or directory

alex@alex-desktop:~/Desktop$ tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz
tar: CJLZ600LE-CUPS-1.0-1.TAR.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

alex@alex-desktop:~/Desktop$ cd ..

alex@alex-desktop:~$ tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz
tar: CJLZ600LE-CUPS-1.0-1.TAR.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

alex@alex-desktop:~$ sudo tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz
tar: CJLZ600LE-CUPS-1.0-1.TAR.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

alex@alex-desktop:~$ cd Desktop

alex@alex-desktop:~/Desktop$ sudo tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz
tar: CJLZ600LE-CUPS-1.0-1.TAR.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

alex@alex-desktop:~/Desktop$ ls
lexmark

alex@alex-desktop:~/Desktop$ cd lexmark

alex@alex-desktop:~/Desktop/lexmark$ sudo tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz
tar: CJLZ600LE-CUPS-1.0-1.TAR.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

alex@alex-desktop:~/Desktop/lexmark$ tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz
tar: CJLZ600LE-CUPS-1.0-1.TAR.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

alex@alex-desktop:~/Desktop/lexmark$ ls
COPYING  README  z600cups-1.0-1.gz.sh

alex@alex-desktop:~/Desktop/lexmark$ sudo tar -xvzf z600LE-CUPS-1.0-1.TAR.gz
tar: z600LE-CUPS-1.0-1.TAR.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

alex@alex-desktop:~/Desktop/lexmark$ sudo tar -xvzf z600-CUPS-1.0-1.TAR.gz
tar: z600-CUPS-1.0-1.TAR.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

alex@alex-desktop:~/Desktop/lexmark$ sudo tar -xvzf z600CUPS-1.0-1.TAR.gz
tar: z600CUPS-1.0-1.TAR.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

alex@alex-desktop:~/Desktop/lexmark$ sudo tar -xvzf z600cups-1.0-1.TAR.gz
tar: z600cups-1.0-1.TAR.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

alex@alex-desktop:~/Desktop/lexmark$ cd ..
alex@alex-desktop:~/Desktop$ sudo tar -xvzf z600cups-1.0-1.TAR.gz
tar: z600cups-1.0-1.TAR.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
```

i just dont get this untarring stuff, and yeah i,ve read up on it, in theory its simple but for me rarely works, i know its a simple solution to this and iam doing something fundamentally wrong and its all my mistakes and all that but any how-to that involves untarring tells me to not bother

there was more in terminal but didnt want to bore you ;)

---

### Post by Najand on 2007-04-30
It seems it has been already untared and it is in:&#12288;~/Desktop/lexmark

---

### Post by klytu on 2007-04-30
> **mills said:**
> this why i couldnt be bothered, i have the driver in a folder on the desktop

```
alex@alex-desktop:~$ mv CJLZ600LE-CUPS-1.0-1.TAR.gz lexmark
mv: cannot stat `CJLZ600LE-CUPS-1.0-1.TAR.gz': No such file or directory

alex@alex-desktop:~$ cd Desktop

alex@alex-desktop:~/Desktop$ mv CJLZ600LE-CUPS-1.0-1.TAR.gz lexmark
mv: cannot stat `CJLZ600LE-CUPS-1.0-1.TAR.gz': No such file or directory

alex@alex-desktop:~/Desktop$ tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz
tar: CJLZ600LE-CUPS-1.0-1.TAR.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

alex@alex-desktop:~/Desktop$ cd ..

alex@alex-desktop:~$ tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz
tar: CJLZ600LE-CUPS-1.0-1.TAR.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

alex@alex-desktop:~$ sudo tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz
tar: CJLZ600LE-CUPS-1.0-1.TAR.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

alex@alex-desktop:~$ cd Desktop

alex@alex-desktop:~/Desktop$ sudo tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz
tar: CJLZ600LE-CUPS-1.0-1.TAR.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

alex@alex-desktop:~/Desktop$ ls
lexmark

alex@alex-desktop:~/Desktop$ cd lexmark

alex@alex-desktop:~/Desktop/lexmark$ sudo tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz
tar: CJLZ600LE-CUPS-1.0-1.TAR.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

alex@alex-desktop:~/Desktop/lexmark$ tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz
tar: CJLZ600LE-CUPS-1.0-1.TAR.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

alex@alex-desktop:~/Desktop/lexmark$ ls
COPYING  README  z600cups-1.0-1.gz.sh

alex@alex-desktop:~/Desktop/lexmark$ sudo tar -xvzf z600LE-CUPS-1.0-1.TAR.gz
tar: z600LE-CUPS-1.0-1.TAR.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

alex@alex-desktop:~/Desktop/lexmark$ sudo tar -xvzf z600-CUPS-1.0-1.TAR.gz
tar: z600-CUPS-1.0-1.TAR.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

alex@alex-desktop:~/Desktop/lexmark$ sudo tar -xvzf z600CUPS-1.0-1.TAR.gz
tar: z600CUPS-1.0-1.TAR.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

alex@alex-desktop:~/Desktop/lexmark$ sudo tar -xvzf z600cups-1.0-1.TAR.gz
tar: z600cups-1.0-1.TAR.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

alex@alex-desktop:~/Desktop/lexmark$ cd ..
alex@alex-desktop:~/Desktop$ sudo tar -xvzf z600cups-1.0-1.TAR.gz
tar: z600cups-1.0-1.TAR.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
```

i just dont get this untarring stuff, and yeah i,ve read up on it, in theory its simple but for me rarely works, i know its a simple solution to this and iam doing something fundamentally wrong and its all my mistakes and all that but any how-to that involves untarring tells me to not bother

there was more in terminal but didnt want to bore you ;)

You are using the tar command on a file that is not tarred.  Look at this line: > alex@alex-desktop:~/Desktop/lexmark$ ls
COPYING  README  z600cups-1.0-1.gz.sh and you did this:> alex@alex-desktop:~/Desktop/lexmark$ cd ..
alex@alex-desktop:~/Desktop$ sudo tar -xvzf z600cups-1.0-1.TAR.gz Now that you have extracted z600cups-1.0-1.gz.sh, navigate to your /Desktop/lexmark directory and do an ```
ls -l
``` once there to make sure you are in the correct place and then continue wih the instructions from the HowTo: > $ tail -n +143 z600cups-1.0-1.gz.sh > install.tar.gz # the sh script is broken for newer systems. use `tail` to extract the binary portion of the script.
$ tar -xvzf install.tar.gz # extract the contents produced by tail
$ alien -t z600cups-1.0-1.i386.rpm # convert unusable rpm packages to tgz.
$ alien -t z600llpddk-2.0-1.i386.rpm # convert unusable rpm packages to tgz.
$ sudo tar xvzf  z600llpddk-2.0.tgz -C / # extract the tgz's to / putting the files in their right place
$ sudo tar xvzf z600cups-1.0.tgz -C / # extract the tgz's to / putting the files in their right place
$ sudo ldconfig # DO NOT SKIP THIS STEP or your printer backend won't find required libraries
$ cd /usr/share/cups/model
$ sudo gunzip Lexmark-Z600-lxz600cj-cups.ppd.gz # unzip the ppd, which should _not_ be gzipped

---

### Post by mills on 2007-04-30
is this supposed to happen

&#65533;1&#65533;&#65533;&#65533;&#28766;&#65533;&#65533;&#65533;&#65533;QV  7&#65533;&#65533; &#705;bT&#65533;s&#65382;
&#65533;&#65533;&#65533;D7.B?&#65533;#(&#65533;z.&#65533;&#65533;&#65533;IX&#65533;%&
^@N&#65533;5&#65533;&#65533;{p&#65533;&#65533;&#65533;&#65533;T r/&#65533;KM&#65533;|&#65533;LdE&#65533;g&#1040;&#65533;N&#65533;&#65533;&#65533;C+&#65533;
&#65533;C!&#65533;&#65533;&#65533;&#65533;&#65533; +&#65533;_&#65533;
                    Gg¹æøà¯AAú11"rPÈweÅä ìÛ&#8226;£5<îUÆc¿æS
                                                         ðEÌ&#381;&#8364;Å¸2ÇS&#8222;çüã+&#8249;ætläbâ×¥&#382;5üæp8¨&#8211;ÓÜKÏÄ&#8221;&#710;»õ
                             ©
                              &#402;¬&#353;&#8250;     °ZCmÅÀ&#8249;&#8218;yßò&#8225;Qâµå.n¥Yu&#8230;«&#8230;¦"GZÙæø°eÏ&#8211;°ÄõOBÒ&#8222;dd¥õEp ¤BÆ&#8220;B=Ú?Eá§&#8482;Ç§""¡ &#732;&#353;&#353;¢#&%¡¡¢
¢êæzptpzÈÏÚ·®k&#65533;&#65533;&#65533;&#65533;&#65533;A,cm&#65533;&#65533;&#65533;ww}:X&#65533;&#1251;!M&#65533;[0,&#65533;&#65533;&#1832;&#65533;(5~yEi&#65533;&#65533;F&#65533;&#65533;ik&#65533;&#65533;&#65533;ÓT&#65533;&#65533;c&#65533;&#65533;&#65533;&#65533;n",&#65533;&#65533;jb~&#65533;&#65533;&#65533;Fz&#65533;B&#65533;(l&#65533;}S&#65533;&#65533;&#65533;&#937;.&#65533;}r&#1628;oba&#65533;&#65533;$4b&#65533;&#65533;Q&#65533;m

&#65533;%¬¢oü3
ØUÑòGX&#338;ò×ÒTøåãB&#8217;O _Ôq&#65533;c&#65533;Q`e6_
&#8226;ìöÈÁABÃDGIyåM-)    Ø
                         bjBÚ¢òÊZÄ?::"JrÂpÜ ¡9GFFÅÇECÁoïÿù¾&#8249;
                                                              HHXX&#732;&#338;C À#"  ¢&%++¥¢ &#382;"!"ú«Ê¨&#8364;R&#8364;&#402;£åùã'ç¬-È'$ë³º
&#353;Ùò&#732;Ã0Ü&#8249;&#8250;w&#8221;&V: ØøÆ0ØP;G&#8220;eÔfv·ãÃÅ'2.63sR2&#382;æù×¨x
                                                    fÄÊJI(úC!F&#382;DcBvÆOß§ðW²#õÄ·gG¦Ö$Äãaää&#382;GILRVÅ¡§Ã&#8220;ýÅÀ¼>&#8230;²   NG?·$&#732;üWk-Î±²222Ð/,ª&#8222;XÓ&#8220;£
                                                                 ;ÆssskcK;!=µ0$4,8Öý&#8226;þ(®¬*(Å¥Â£¤&&§&#339;Ä&#8216;øhP8$
                               ö$þ
                                   )-ô«J* X(&#338;Úà&#8211;&#338;&#8364;ÒÄftD)qdgÔ¶eåDÉ¢ZZrjBjc«Ø;xA_ÀFô&#381;ë&#8482;ç&úÈóF&#8211;= eq-$  _ÜØÚÂí&#382;&#732;&#8222;Ðlôd&#8250;1ÆÂ©Iü°G
                                                         ÷ø&#352; &#8217;&©Éª
.vöõ*ÍIòrK¬LÍMNÎ®öNv®Í-rø§EÆ6G'7'&#8225;æ&#8211;ä¥ÆLÎQUØYÚs0-)$â ÎÚ&#710;&#8217;&#353;&#353;&#339;&#732;&#8221;ÄS¤&#352;r«+,&#402;&#8226;ièæf&#8364;&#402;¢&#353;&#353;&#8217;&#8217;
&#65533;&#65533;&#65533;&#65533;]m=!&#8211;çúÆÄªUA&#65533;&#65533;&#65533;m&#65533;&#65533;&#65533;&#65533;&#65533;O&#8230;%&#338;&#382;ºÐBhFü;5/'`c&#65533;DCC&#65533;q&#65533;qI&#65533;&#65533;
Xo&#65533;&#65533;|Bp&#55427;&#57130;n&#65533;  bqUX>4+`
{&#65533;&#65533;&#65533;&#423;&#65533;&#65533;&#65533;m/p&#65533;7Äü&#8240;ñÅùÁÑÙÙÕÉ©±&#8482;*¥u¾¾µÅÝõåå¥±Í¹&#8482;&#8240;*µ¹¾1ä3(qABÆVRMGCnCmoACCBÄ®løÅWRKEnjgh*m1&#352;øgûfÆ&#8230;Ue¡&#8225;ÿ¸Êï-,j¨f¥¤¼"n&#8224;©³¹XQ       Â"ÆF3µ"5©u      &#8482;-ÿ+-%%öN *.B¾ÁÝå¹YaP.2&NEXõØÆ;·§&#8249;··¶µspÃq·¸ØðèÈXÅ,$+ÆXò&#8240;ÿøyúzúx<¿&#382;qëj«,îï AÁÀï®í.®8&#8212;&#732;ÚüüÖÎ/óüÜÒÈ ØâQ<çºú¨H-ä½ckK=cSåk&#402;¨/&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;<&#65533;&#65533;&#65533;f&#65533;&#65533;A&#65533;&#65533;&#65533;*&#65533;g&#65533;&#65533;&#65533;&#65533;&#684;&#65533;.R
           d&#65533;&#65533;&#65533;&#65533;&#338;Î$ÖÒêHðæÇfæ¹e9e ×ô&#338;vçòÚÆ¤¸&#732;hßcköò»¼&#8212;
                                                         Ë5Z±ë&#8240; q°ç&ºel>y&#339;hÏV#Ò7µK ½ânÿâÛ¿t+¤IÆVÇGÅ
&#8224;&#352;&#352;                       D(
&#352;&#8240;ÒUÙÜß&#8225;«Ä%Vcãâ2buövp&#65533;a&#65533;T!UQ&#65533;EL/p25&#65533;&#65533;&#65533;&#65533;aeg!MC&#65533;&#65533;2&#65533;&#65533;n&#65533;&#1041;ZI     &#65533;&#65533;&#843;&#65533;&#65533;&#65533;zJBR^^V&#65533;u,&#65533;&#65533;&#361;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;]W3]&#65533;&#65533;&#65533;uzc&#65533;&#65533;q,&#65533;&#812;&#65533;&#65533;&#65533;[@&#65533;\&#65533;rs&#65533;|7&#65533;&#65533;W&#65533;?&#65533;&#65533;A&#65533;&#65533;&#65533;&#65533;&#65533;"&#65533;&#65533;M}&#65533;&#65533;lJ&#65533;&#65533;d&#16600;&#65533;y`&#65533;[m&#65533;^l0 LÍ&#381;w&#8216;ái&#8240;¹ñàìØkj,µ¾û&#710;&#710;&#352;&#338;,Ç¶c&#8250;&#8240;&#8482;·'¨     õ>3)ß&#402;Valex@alex-desktop:~/Desk2;9;c62;9;c62;9;c62;9;c62;9;c6

there was a hell of alot more of it,

i gone and broke it havent i:(

this command is the culprit - tail -n +143 z600cups-1.0-1.gz.sh > install.tar.gz

EDIT; ignore this post iam just being a plank at the moment, i entered "tail -n +143 z600cups-1.0-1.gz.sh" not the culprit above

---

### Post by klytu on 2007-04-30
> **mills said:**
> is this supposed to happen

&#65533;1&#65533;&#65533;&#65533;&#28766;&#65533;&#65533;&#65533;&#65533;QV  7&#65533;&#65533; &#705;bT&#65533;s&#65382;
&#65533;&#65533;&#65533;D7.B?&#65533;#(&#65533;z.&#65533;&#65533;&#65533;IX&#65533;%&
^@N&#65533;5&#65533;&#65533;{p&#65533;&#65533;&#65533;&#65533;T r/&#65533;KM&#65533;|&#65533;LdE&#65533;g&#1040;&#65533;N&#65533;&#65533;&#65533;C+&#65533;
&#65533;C!&#65533;&#65533;&#65533;&#65533;&#65533; +&#65533;_&#65533;
                    Gg¹æøà¯AAú11"rPÈweÅä ìÛ•£5<îUÆc¿æS
                                                         ðEÌŽ€Å¸2ÇS„çüã+‹ætläbâ×¥ž5üæp8¨–ÓÜKÏÄ”ˆ»õ
                             ©
                              ƒ¬š›     °ZCmÅÀ‹‚yßò‡Qâµå.n¥Yu…«…¦"GZÙæø°eÏ–°ÄõOBÒ„dd¥õEp ¤BÆ“B=Ú?Eá§™Ç§""¡ ˜šš¢#&%¡¡¢
¢êæzptpzÈÏÚ·®k&#65533;&#65533;&#65533;&#65533;&#65533;A,cm&#65533;&#65533;&#65533;ww}:X&#65533;&#1251;!M&#65533;[0,&#65533;&#65533;&#1832;&#65533;(5~yEi&#65533;&#65533;F&#65533;&#65533;ik&#65533;&#65533;&#65533;ÓT&#65533;&#65533;c&#65533;&#65533;&#65533;&#65533;n",&#65533;&#65533;jb~&#65533;&#65533;&#65533;Fz&#65533;B&#65533;(l&#65533;}S&#65533;&#65533;&#65533;&#937;.&#65533;}r&#1628;oba&#65533;&#65533;$4b&#65533;&#65533;Q&#65533;m

&#65533;%¬¢oü3
ØUÑòGXŒò×ÒTøåãB’O _Ôq&#65533;c&#65533;Q`e6_
•ìöÈÁABÃDGIyåM-)    Ø
                         bjBÚ¢òÊZÄ?::"JrÂpÜ ¡9GFFÅÇECÁoïÿù¾‹
                                                              HHXX˜ŒC À#"  ¢&%++¥¢ ž"!"ú«Ê¨€R€ƒ£åùã'ç¬-È'$ë³º
šÙò˜Ã0Ü‹›w”&V: ØøÆ0ØP;G“eÔfv·ãÃÅ'2.63sR2žæù×¨x
                                                    fÄÊJI(úC!FžDcBvÆOß§ðW²#õÄ·gG¦Ö$ÄãaääžGILRVÅ¡§Ã“ýÅÀ¼>…²   NG?·$˜üWk-Î±²222Ð/,ª„XÓ“£
                                                                 ;ÆssskcK;!=µ0$4,8Öý•þ(®¬*(Å¥Â£¤&&§œÄ‘øhP8$
                               ö$þ
                                   )-ô«J* X(ŒÚà–Œ€ÒÄftD)qdgÔ¶eåDÉ¢ZZrjBjc«Ø;xA_ÀFôŽë™ç&úÈóF–= eq-$  _ÜØÚÂíž˜„Ðlôd›1ÆÂ©Iü°G
                                                         ÷øŠ ’&©Éª
.vöõ*ÍIòrK¬LÍMNÎ®öNv®Í-rø§EÆ6G'7'‡æ–ä¥ÆLÎQUØYÚs0-)$â ÎÚˆ’ššœ˜”ÄS¤Šr«+,ƒ•ièæf€ƒ¢šš’’
&#65533;&#65533;&#65533;&#65533;]m=!–çúÆÄªUA&#65533;&#65533;&#65533;m&#65533;&#65533;&#65533;&#65533;&#65533;O…%ŒžºÐBhFü;5/'`c&#65533;DCC&#65533;q&#65533;qI&#65533;&#65533;
Xo&#65533;&#65533;|Bp&#200490;n&#65533;  bqUX>4+`
{&#65533;&#65533;&#65533;&#423;&#65533;&#65533;&#65533;m/p&#65533;7Äü‰ñÅùÁÑÙÙÕÉ©±™*¥u¾¾µÅÝõåå¥±Í¹™‰*µ¹¾1ä3(qABÆVRMGCnCmoACCBÄ®løÅWRKEnjgh*m1ŠøgûfÆ…Ue¡‡ÿ¸Êï-,j¨f¥¤¼"n†©³¹XQ       Â"ÆF3µ"5©u      ™-ÿ+-%%öN *.B¾ÁÝå¹YaP.2&NEXõØÆ;·§‹··¶µspÃq·¸ØðèÈXÅ,$+ÆXò‰ÿøyúzúx<¿žqëj«,îï AÁÀï®í.®8—˜ÚüüÖÎ/óüÜÒÈ ØâQ<çºú¨H-ä½ckK=cSåkƒ¨/&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;<&#65533;&#65533;&#65533;f&#65533;&#65533;A&#65533;&#65533;&#65533;*&#65533;g&#65533;&#65533;&#65533;&#65533;&#684;&#65533;.R
           d&#65533;&#65533;&#65533;&#65533;ŒÎ$ÖÒêHðæÇfæ¹e9e ×ôŒvçòÚÆ¤¸˜hßcköò»¼—
                                                         Ë5Z±ë‰ q°ç&ºel>yœhÏV#Ò7µK ½ânÿâÛ¿t+¤IÆVÇGÅ
†ŠŠ                       D(
Š‰ÒUÙÜß‡«Ä%Vcãâ2buövp&#65533;a&#65533;T!UQ&#65533;EL/p25&#65533;&#65533;&#65533;&#65533;aeg!MC&#65533;&#65533;2&#65533;&#65533;n&#65533;&#1041;ZI     &#65533;&#65533;&#843;&#65533;&#65533;&#65533;zJBR^^V&#65533;u,&#65533;&#65533;&#361;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;]W3]&#65533;&#65533;&#65533;uzc&#65533;&#65533;q,&#65533;&#812;&#65533;&#65533;&#65533;[@&#65533;\&#65533;rs&#65533;|7&#65533;&#65533;W&#65533;?&#65533;&#65533;A&#65533;&#65533;&#65533;&#65533;&#65533;"&#65533;&#65533;M}&#65533;&#65533;lJ&#65533;&#65533;d&#16600;&#65533;y`&#65533;[m&#65533;^l0 LÍŽw‘ái‰¹ñàìØkj,µ¾ûˆˆŠŒ,Ç¶c›‰™·'¨     õ>3)ßƒValex@alex-desktop:~/Desk2;9;c62;9;c62;9;c62;9;c62;9;c6

there was a hell of alot more of it,

i gone and broke it havent i:(

this command is the culprit - tail -n +143 z600cups-1.0-1.gz.sh > install.tar.gz

Weird. It looks like the command output the binary contents but didn´t redirect to the file install.tar.gz. Did you cut and paste the command or did you type it? What is the output of ```
ls -l
``` at the moment in your /Desktop/lexmark directory?

---

### Post by mills on 2007-04-30
ok iam back to spuare 1 installed the drivers everything went smoothly but still when i go to system - admin - printers to start printing its tellin me about a ppd file again
 

ps i appreciate this klytu

---

### Post by mills on 2007-04-30
ok i give up iam stickin to windows for printing

cheers for the help tho guys

---

### Post by klytu on 2007-04-30
> **mills said:**
> ok i give up iam stickin to windows for printing

cheers for the help tho guys

I can understand if you are frustrated not getting this to work, but did you complete all the steps in the HowTo? Specifically, after installing the driver did you do:```
/etc/rc2.d/S19cupsys restart
``` and then: ```
/etc/rc2.d/S19cupsys restart
./z600
``` What was the output of ```
./z600
``` I wanted to make sure you completed those steps (and also tried the suggestion for what to do if there was no output) before you gave up. 

I used to use a Lexmark X73 all-in-one that was VERY difficult to get working in Linux. I used that HowTo as a guide, changed some specifics and got it to print, although I never got scanning working. Eventually color printing failed in the X73. I found out that repairing it wasn't worth the cost and replaced it with an HPC3180 all-in-one which works right out of the box in Fiesty.

---

