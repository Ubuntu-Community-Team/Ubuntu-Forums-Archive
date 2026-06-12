---
title: "Lying to firefox about flash?"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by xpod on 2006-09-10
good morning people....OR afternoon morelike
                                            I seen a post somewhere that said
it was quite easy to lie to firefox about which version of flash was installed.......SO by going to /home/username/.mozilla/firefox and opening the "pluginreg.dat" file and chaging all instances of "shockwave flash 7.0"
to "shockwave flash 9.0" we can apparently fool FF.

The sites that require version 9.0 specifc features are few and far between i  believe?

SO....IS this ok to do or should i just wait till 9.0 is out for ubu?(or just install 8.0????)......choices choices:confused: 

It`s not that i NEED 9.0 but if it`s possible i`d like to try it at least.

PLUS.....ALL ive had to "edit" up till now is my sources list,the details of which i copied from another thread.

---

### Post by kostkon on 2006-09-10
Yes, just do it, why not. And it is very very simple. You don't even need to do *sudo* or to use the CLI. Just go and open the file with gedit.

---

### Post by xpod on 2006-09-10
Thanks...i`ll go give it a go:-k 
As i said i aint had to edit much but i reckon i can manage this ok.I just wanted to know it would`nt be a "bad" idea.

Cheers

---

### Post by EdThaSlayer on 2006-09-10
Well...you may tell those servers that you are using flash 9 but then again...it wont work correctly(errors and such will happen) so i recommend that you just wait till the "real fully capable" flash 9 appears.

And i thought that only flash 7 was out at the moment.

---

### Post by xpod on 2006-09-10
Just to check............does this seem right??

Generated File. Do not edit.

[HEADER]
Version:0.08:$

[PLUGINS]
/usr/lib/firefox/plugins/nphelix.so:$
:$
1157033023000:1:5:$
Helix DNA Plugin: RealPlayer G2 Plug-In Compatible version 0.4.0.622 built with gcc 3.3.5 on Jul 18 2006:$
Helix DNA Plugin: RealPlayer G2 Plug-In Compatible:$
1
0:audio/x-pn-realaudio-plugin:RealPlayer Plugin Metafile:rpm:$
/usr/lib/flashplugin-nonfree/libflashplayer.so:$
:$
1157550568000:1:5:$
Shockwave Flash 9.0 r63:$
Shockwave Flash:$
2
0:application/x-shockwave-flash:Shockwave Flash:swf:$
1:application/futuresplash:FutureSplash Player:spl:$


There was only the one instance of it mentioned but i have changed it as you can see.Is THAT it?...........and there was me ready to go try installing 8.0 the hard way:D

EDIT:....do you know a specific site that need 8 or 9 that i could check on?thanks

EDIT":...works fine with usual`s...i.e google & you tube

---

### Post by xpod on 2006-09-10
Im just "assuming" theres an 8 if people are talking about 9 comming.
It`s just a number to me mate....and i like playing with numbers:-D

Well ive been round a few sites with flash and no probs whatsoever....yet:D 

Whether any of them were 7,8 or 9 specific i dont know but i know i used to mabey have probs every few sites with just 7 but i aint been stopped with this yet so...........................?????????

---

