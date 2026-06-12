---
title: "Networking Crashes Every Time"
date: 2005-09-27
forum: Absolute Beginner Talk
---

### Post by Nihilist on 2005-09-27
i installed ubuntu the other day. i have another post up here about a monitor problem, and a potential solution. only trouble is, im reduced to using windows because the networking program crashes every time i click on it.

i goto system, administrator and click on networking. according to the help guide, thats where id go to set up my dsl stuff. but, i cant get do that if i cant access it lol.

any workarounds for it? or do i just scrap ubuntu  until i can get breezy and hope the problem is solved then?

---

### Post by cwaldbieser on 2005-09-27
[QUOTE=Nihilist]i installed ubuntu the other day. i have another post up here about a monitor problem, and a potential solution. only trouble is, im reduced to using windows because the networking program crashes every time i click on it.

i goto system, administrator and click on networking. according to the help guide, thats where id go to set up my dsl stuff. but, i cant get do that if i cant access it lol.

any workarounds for it? or do i just scrap ubuntu  until i can get breezy and hope the problem is solved then?[/QUOTE]

Everything can be set up by editing some config files if you feel up to it.  Not sure whay the GUI is dying on you...

If you type the following commands in the terminal, it will create some files you can copy to a floppy or other drive an then post back here so we can advise you:
```

$ ifconfig -a > interfaces.txt
$ route > routes.txt

```
Also, since you are using Windows, you might as well get the config info from that for comparison.  In CMD.EXE, type:
```

C:\> ipconfig
C:\> route print

```
and post the results along side those from Ubuntu.

---

### Post by Nihilist on 2005-09-28
root terminal crashes. in a normal terminal i tried those commands and nothign happened. when i tried to su, it said my password was wrong.

could this justbe a bad CD o something? theres only one password, so id have a hard time forgetting it.

---

### Post by Nihilist on 2005-09-28
bump

---

### Post by cwaldbieser on 2005-09-28
[QUOTE=Nihilist]root terminal crashes. in a normal terminal i tried those commands and nothign happened. when i tried to su, it said my password was wrong.
could this justbe a bad CD o something? theres only one password, so id have a hard time forgetting it.[/QUOTE]
You should not need root access to run those commands to query the present state of the network-- only when trying to modify it.  You could try using "sudo" (not "su"), but I don't see why that would make a difference.

```
$ sudo ifconfig -a
```

---

### Post by Nihilist on 2005-09-29
anytime i do a command with $ on it it errors. ill try it and report back here later. ive tried all the commands given with and without $.

i also went to terminal and typed in network-admin and the networking tab came up, but never fully loaded. additionally, on the  live CD the networking tab works fine, so i tried configuring the pppo thing. i had it autofind or configure or whatever the modem and it said it couldnt find it, but im not sure if it was talking about the 56k. the dsl modem is a westell 6100. the 56k modem is a lucent winmodem.

im really lost here.

---

### Post by Nihilist on 2005-09-29
lemme bounce this up a bit.

---

### Post by aran384 on 2005-09-29
my soultion would be reinstall , if u just installed it.... 

if you got data i dont know....

maybe u should try thos commands in recorvery mode. ??? from bootup in grub ?

---

### Post by DaveBr on 2005-09-29
I believe this is the same problem as described here, which I am struggling with.... [http://ubuntuforums.org/showthread.php?t=21629](http://ubuntuforums.org/showthread.php?t=21629)

Basically the default user (as set up during install) cannot access any administration GUIs.....

No doubt this could be solved by activating root and editing confg files from terminal, but this doesn't really seem like a solution to a desktop feature that is supposed to work 'out-of-the-box' as default user.

If anyone has any suggestions how to get the administration GUIs working it would be appreciated.

Dave (frustrated newbie!).

---

### Post by Nihilist on 2005-09-29
yea i think ill try to reinstall it over the old partition sometime soon.

---

### Post by cwaldbieser on 2005-09-29
[QUOTE=Nihilist]anytime i do a command with $ on it it errors. ill try it and report back here later. ive tried all the commands given with and without $.
i also went to terminal and typed in network-admin and the networking tab came up, but never fully loaded. additionally, on the  live CD the networking tab works fine, so i tried configuring the pppo thing. i had it autofind or configure or whatever the modem and it said it couldnt find it, but im not sure if it was talking about the 56k. the dsl modem is a westell 6100. the 56k modem is a lucent winmodem.
im really lost here.[/QUOTE]
Sorry.  The "$" is just the terminal prompt.  It is like "C:\>" in Windows.  The "#" is the root prompt.  So for example:
```

$ gedit myfile.txt
$ sudo bash
# gedit rootfile.txt

```
The above commands would mean
1) (At the normal prompt) edit myfile.txt with gedit.
2) (At the normal prompt) start a root bash shell.
3) (At the root prompt) edit rootfile.txt as the root user.

You don't type the "$" or the "#"-- they are just shorthand used so people don't always have to say, "at the prompt, type ...".

---

