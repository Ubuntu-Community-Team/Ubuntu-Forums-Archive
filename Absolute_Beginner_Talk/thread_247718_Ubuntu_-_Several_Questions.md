---
title: "Ubuntu - Several Questions"
date: 2006-08-31
forum: Absolute Beginner Talk
---

### Post by MaLaKa on 2006-08-31
Okay I just got ubuntu, Ive installed it with the help of a friend over the net on my other pc. All runs well so far. I just have a few questions (alas some are going to be retarded). So here they are!


Drivers - Im not 100% sure if I need to install drivers for my 6600GT, VIA chipset or sound etc. They all seem to run, but rather slow. I did look around and there are forceware drivers for linux but they are all in intel architecture? or athlon64 (alas im on a 2000+ so no 64bit for me). Where can I download these drivers? and how do I go around installing them? 

Permissions - How can I edit a file on my root or any other harddrives? All I can edit so far is my Home drive? This is quite fustrating cause Im trying to save logs onto my windows drive, so I can post some of them on here. But it wont let me :confused: I know I have to have permission to do so, but I only have one main account I use and it is the one I made at the ubuntu install? Help!

Dial up - I know this is prob a broken record on here. Im dialing up and connecting, but then im dropping. Some error about the pppd deamon failing or somthing. I'm using "sudo wvdial" to connect and its all setup. But it just hangs and reconnects. Again I cant post my logs cause I cant save them onto my windows drive haha.. ](*,) (see permissions).

Games - I know linux isnt really a OS made for gaming but I know it can be done. I have seen the install binaries for linux for games like Quake 2,3,4, Doom3 etc. After downloading these install binaries, what are you ment to do? 

Codecs - Well to my suprise, after installing ubuntu I cant play MP3s, Mpegs, AVIs or DVDs! There are no codecs what so ever installed! All I can play are .ogg files D: Again where abouts can I find codecs and how does one install them?


Well those are my main questions and problems. Please help! Also it would be cool if anyone who is well experienced with linux would mind adding me or me adding them to MSN? I seem to have lots of stupid questions that seem to just take up forum space, that could prob be better explained over IM. I find forums are rather.. time consuming. 

Ubuntu 6.06LTS System
Athlon 2000+
GA-7VAXP (F16)
1024mb Corsair PC3200
Sparkle 6600GT 128mb/AGP8X (530/1050)
AC'97 Sound
Netcomm IN5699 

Help!

---

### Post by deadgobby on 2006-08-31
> **MaLaKa said:**
> Okay I just got ubuntu, Ive installed it with the help of a friend over the net on my other pc. All runs well so far. I just have a few questions (alas some are going to be retarded). So here they are!


Drivers - Im not 100% sure if I need to install drivers for my 6600GT, VIA chipset or sound etc. They all seem to run, but rather slow. I did look around and there are forceware drivers for linux but they are all in intel architecture? or athlon64 (alas im on a 2000+ so no 64bit for me). Where can I download these drivers? and how do I go around installing them? 

Permissions - How can I edit a file on my root or any other harddrives? All I can edit so far is my Home drive? This is quite fustrating cause Im trying to save logs onto my windows drive, so I can post some of them on here. But it wont let me :confused: I know I have to have permission to do so, but I only have one main account I use and it is the one I made at the ubuntu install? Help!

Dial up - I know this is prob a broken record on here. Im dialing up and connecting, but then im dropping. Some error about the pppd deamon failing or somthing. I'm using "sudo wvdial" to connect and its all setup. But it just hangs and reconnects. Again I cant post my logs cause I cant save them onto my windows drive haha.. ](*,) (see permissions).

Games - I know linux isnt really a OS made for gaming but I know it can be done. I have seen the install binaries for linux for games like Quake 2,3,4, Doom3 etc. After downloading these install binaries, what are you ment to do? 

Codecs - Well to my suprise, after installing ubuntu I cant play MP3s, Mpegs, AVIs or DVDs! There are no codecs what so ever installed! All I can play are .ogg files D: Again where abouts can I find codecs and how does one install them?


Well those are my main questions and problems. Please help! Also it would be cool if anyone who is well experienced with linux would mind adding me or me adding them to MSN? I seem to have lots of stupid questions that seem to just take up forum space, that could prob be better explained over IM. I find forums are rather.. time consuming. 

Ubuntu 6.06LTS System
Athlon 2000+
GA-7VAXP (F16)
1024mb Corsair PC3200
Sparkle 6600GT 128mb/AGP8X (530/1050)
AC'97 Sound
Netcomm IN5699 

Help!
>>I need to install drivers for my 6600GT, VIA chipset or sound etc. They all seem to run, but rather slow. 
 If it is on board sound you really do not need drivers
[https://wiki.ubuntu.com/?action=fullsearch&context=180&value=sound&titlesearch=Titles](https://wiki.ubuntu.com/?action=fullsearch&context=180&value=sound&titlesearch=Titles)
 As for your dailup
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)
 As for games that you ask on.
[https://help.ubuntu.com/community/DialupModemHowto?action=fullsearch&context=180&value=games&titlesearch=Titles](https://help.ubuntu.com/community/DialupModemHowto?action=fullsearch&context=180&value=games&titlesearch=Titles)
 As for codecs, you will need to install them your self. Codecs are not free and thus Ubie cannot install them on the O/S. So thus you will need to install them. Here is a link to Automatix. Please READ BEFORE INSTALLING.
[http://ubuntuforums.org/showthread.php?t=138405&highlight=Flash+Player](http://ubuntuforums.org/showthread.php?t=138405&highlight=Flash+Player)
[http://ubuntuforums.org/showthread.php?t=138405&highlight=Flash+Player](http://ubuntuforums.org/showthread.php?t=138405&highlight=Flash+Player) 
As for the other question on permissions on such
[http://ubuntuguide.org/wiki/Dapper#limewire](http://ubuntuguide.org/wiki/Dapper#limewire)

There is no such thing of asking stupid questions to help understanding some thing. The only stupid thing is not asking at all.

gobby

---

### Post by pyros on 2006-08-31
> **MaLaKa said:**
> 
Drivers - Im not 100% sure if I need to install drivers for my 6600GT

Am I correct that's an nvidia card? You would probably want to install the non open source drivers. go to the unofficial ubuntu starter guide at [http://www.ubuntuguide.org/](http://www.ubuntuguide.org/) (section 11.2) for some guidence in the steps necessary.

> **MaLaKa said:**
> 
Permissions - How can I edit a file on my root or any other harddrives?
the best way to do this will depend on what kind of program you are looking to use. on the applications menu, there is an entry for "run as different user" you can use that to launch nautilus, the gnome file manager. just type nautilus under run, leave root as the user and click ok. it will ask you for your password and then launch the filemanager.

> **MaLaKa said:**
> 
Games - I know linux isnt really a OS made for gaming but I know it can be done. I have seen the install binaries for linux for games like Quake 2,3,4, Doom3 etc. After downloading these install binaries, what are you ment to do? 

usually, you just run the binary.

> **MaLaKa said:**
> 
Codecs - Well to my suprise, after installing ubuntu I cant play MP3s, Mpegs, AVIs or DVDs! There are no codecs what so ever installed! All I can play are .ogg files D: Again where abouts can I find codecs and how does one install them?

The unofficial ubuntu starter guide (section 6.20) should give you instructions on installing these.

---

### Post by MaLaKa on 2006-08-31
Everything im trying to do requires an internet connection. Is there any way to actually download the files then install them?

---

### Post by deadgobby on 2006-08-31
well alot has to DL from the net, but Ubie understands. 
[https://ubuntuplus.bountysource.com/](https://ubuntuplus.bountysource.com/)
 This is a add on CD ISO for people who use dail up.

---

### Post by steve.horsley on 2006-08-31
You are right - Ubuntu without the net is a rather sad thing. It's probably best to concentate on getting the network going first. You will not be able to copy the error message to the windows drive - MS won't publish the NTFS spec. You are probably best off copying to a USB stick to transter stuff to windows. If you need to, you can read from NTFS though. See the link below for how to mount windows drives:
[http://ubuntuguide.org/wiki/Dapper#Windows](http://ubuntuguide.org/wiki/Dapper#Windows)

You will probably need to edit config files outside of your home dir. Use the command sudo in front of commands to get the extra priviledge required, e.g.
sudo gedit /etc/WhateverItsCalled

---

