---
title: "Windows -&gt; Ubuntu : step 1"
date: 2006-08-23
forum: Absolute Beginner Talk
---

### Post by Janov Pelorat on 2006-08-23
Hello.

Hope I'm in the right place : absolute beginner does correspond to my skills though.

I'm a kind of Windows advanced user since I use it since v3.0 and used DOS since v4.0. But, I know nothing about programming (execpt simple .bat files).

One of my computer runs WinXP and is used for :
- MSN (no cam, but sounds, animated stuff and colored text required. Also, file transfer required)
- Surf (Firefox)
- Listening music (stored on a network windows-based machine)
- Photos (viewing, modifying to create windows wallpaper)
- Mail (Thunderbird)
- MS Office (Word, PPT)
No strange hardware or peripherals. This computer connects to the net througt ethernet to reach a windows-based machine acting like a gateway.

Already done :
- install Ubuntu on a logical partition onto the hard drive already hosting windows. Installation went great and easy : never seen an OS installing as easy as Ubuntu. Great job !
- update the system (great windows update like : I noticed it updates system + software. Great job again).
- find how to install new software (Synaptics). Not so easy to find. It works fine, but I guess the way to get to it could be made easier (I had to understand that adding/removing software is different form a "thing" called Synaptics).

Well, it works :D 

Problems :
- can't make amsn work : it always tells me the login/password is wrong (it is right) and doesn't connect. MSN is "a matter of life" on this machine (teenager's). Ubuntu or any other Linux will be banned if this damned thing doesn't work :rolleyes: 
- I have problems with the keyboard (wire) : all keys are OK except "²" (the key before "1") that is typed "ù". And ALL alternate keys (reached by altGr + a key) do not work (@\|[]}{# unreachable). All these symbols are the third symbols located on the numeric keys above the alpha keys (French keyboard inside).
- can't "mount" networked shared folders held by a windows-based machine over my home ethernet network (samba is installed, I try to connect to the "server" but I can a kind of explorer that leads me to my network folder, but I can't set it up to mount it).

Please help me through this and I'll be able to definitely switch this machine to Ubuntu. And then, I'll try to switch my other 3 machines progressively. Also, I know Linux is more secure than Windows, but this user is kind of "I click everywhere to see what it does" : I guess an antivirus software could be useful;) 

Thanks for your help

---

### Post by rowanparker on 2006-08-23
About aMSN, did you install TLS?

---

### Post by Janov Pelorat on 2006-08-23
well, before I found the synaptics, I tried to download it directly from its website. Chose a wrong linux version before I got one that could be uncompressed by he system. After that, I couldn't find how to install it (setup.exe doesn't seem to be existing with linux :d)

So when I found synaptics, I got it installed that way. First, it refused to start because of a "tlstlc error". Then I did I don't know what (checking every "ubuntu something" in a list : I guess it is used to make synaptics go to the net to get apps to list and then download). After that, amsn didn't asked for anything else. But it doesn't want to connect.
I tried using http port 80 in case there is a firewall blocking, but it doesn't help. I read SSL is required, so it is checked in amsn settings.

---

### Post by Bauer87 on 2006-08-23
I'm a beginner too so I don't know how to handle with your problems concerning the network. (I've had no problems with that.) But accoding to your problems with your keyboard: Have you tried out to reconfigure it (System-->Preferences-->Keyboard; don't know if the menues are called exactly like this because I use the German Ubuntu)?
The problem with aMSN is easy to solve: don't use it. I never used MSN but Gaim on windows as well, it supports ICQ/AIM, MSN, Yahoo and many more chat networks. Never tried out the MSN-Part of it but it should work.

---

### Post by Janov Pelorat on 2006-08-23
For the keyboard, I tried to look for a different layout, but none seems to be ok. During install, I chose French and Latin-9 (if I remember well), which were the default detected by the system.

Concerning amsn/gaim, I just don't care about the program. The important point is : colored text, smilies, animated smilies and file transfers. No webcam support needed. I just neeed the msn-style because my teenage girl *requires* it (otherwise, this place will turn into Tchernobyl :rolleyes:)

---

### Post by Rhubarb on 2006-08-23
Just confirming that MSN works very well in GAIM.  File transfers work, though not super fast (I think the file gets sent to the MSN server then to your buddy, rather than a direct P2P file transfer).

Accessing your windows share just requires some perserverence, you may have to setup a password on your windows machine to get it to work.

---

### Post by mssever on 2006-08-23
To look for relevant error messages in aMSN, Pop open a terminal (Applications > Accessories > Terminal) and type in the command to start it--probably amsn, though I've never used MSN, so I don't know for sure. If there are errors, you'll probably see them in the terminal window.

When it comes to mounting shared SMB folders, you have a couple of options: If you're just using Nautilus, navigate to the appropriate share (Ctrl+L, type smb://) and drag the folder to the sidebar. The other option to really mount them is to install smbmount and edit your /etc/fstab. Read man smbmount for more info. I've never done this, so I can't be more specific.

EDIT: is it smbmount, or smbfs? I don't remember...

---

### Post by Janov Pelorat on 2006-08-23
Keyboard : I made a mistake.
In local, the keyboard just works fine.
I used tightVNC to remote control the linux box (remote desktop on the linux box). The keyboard layout problem is only with the remote session.

---

### Post by Janov Pelorat on 2006-08-23
amsn
attempt to provide package tls 1.5 failed : package tls 1.50 provided instead

---

### Post by rowanparker on 2006-08-23
Saying "don't use aMSN" is not a very good way of solving his problem.
If you want an MSN replacement, aMSN is the answer.

---

### Post by derred on 2006-08-23
About the network folder sharing: Are you talking about a windows network?

If so than try installing smb4k. It is a GUI for samba, and uses the smb protocol to comunicate to windows machines, even let's you choose a workgroup. 

If you don't like Gaim you can also try Kopete although it's not as polished(don't know about sound or file transfer). 
There are always the web-based clients like my personal favorite: [wwwm.meebo.com]("http://wwwm.meebo.com/") (AJAX based)

Hope this helps solve some of your troubles.

---

### Post by Janov Pelorat on 2006-08-23
> **mssever said:**
> To look for relevant error messages in aMSN, Pop open a terminal (Applications > Accessories > Terminal) and type in the command to start it--probably amsn, though I've never used MSN, so I don't know for sure. If there are errors, you'll probably see them in the terminal window.

When it comes to mounting shared SMB folders, you have a couple of options: If you're just using Nautilus, navigate to the appropriate share (Ctrl+L, type smb://) and drag the folder to the sidebar. The other option to really mount them is to install smbmount and edit your /etc/fstab. Read man smbmount for more info. I've never done this, so I can't be more specific.

EDIT: is it smbmount, or smbfs? I don't remember...

For the shared folders, I got it !
I wanted to specify the path as \\serveur\share\folder
Ubuntu just make it easier as I just had to enter the data in the different fields with the \\ and \ ](*,)

---

### Post by Bauer87 on 2006-08-23
> **rowanparker said:**
> Saying "don't use aMSN" is not a very good way of solving his problem.
If you want an MSN replacement, aMSN is the answer.
Yes, it doesn't solve the problems with aMSN but it allows him to chat which is his main "problem" I think. I just tried to help but I have no idea how to fix aMSN, as I said: I'm a noob myself.

---

### Post by Janov Pelorat on 2006-08-23
I can already chat with gaim.
Seems ok, except those color codes they put in their "citations" : they don't display in color and show all the color codes instead.

OK, it's esthetics. Just come in to explain that to a teenage girl :d

---

### Post by seshomaru samma on 2006-08-23
For aMSN try [this]("http://www.ubuntuforums.org/showthread.php?t=216689")

---

### Post by Janov Pelorat on 2006-08-23
> **seshomaru samma said:**
> For aMSN try [this]("http://www.ubuntuforums.org/showthread.php?t=216689")

Synaptics doesn't hold either tcl 8.5, tk 8.5 or amsn 0.97 :confused: 
8.4 of tcl and tk are already installed, as well as 0.95 amsn

Would this solve my connection problem ? The linked thread only talks about esthetics

---

### Post by Janov Pelorat on 2006-08-23
Well.
I finally installed easyubuntu and now amsn works fine.

Next problem : there is no sound :/
Motherboard : [http://www.asrock.com/product/K7S8X.htm](http://www.asrock.com/product/K7S8X.htm)
AC97 chipset. It should work, but it doesn't (works fine in windows)

Any idea ?

---

### Post by mssever on 2006-08-24
> **Janov Pelorat said:**
> Next problem : there is no sound :/
Motherboard : [http://www.asrock.com/product/K7S8X.htm](http://www.asrock.com/product/K7S8X.htm)
AC97 chipset. It should work, but it doesn't (works fine in windows)

Any idea ?

First, the easy stuff. Have you checked the volume and made sure it isn't muted?

Otherwise, I don't know what to tell you for sure, but there are a few places you can check for error messages, which you can paste into Google and see what you get.

First, go to /var/log. This is where (most of) the system's logs live. In that directory, have a look at messages and syslog for starters. Also, check out dmesg. This is where the boot messages live. I've got the following in my /var/log/dmesg:
```
[17179599.132000] AC'97 1 does not respond - RESET
[17179599.132000] AC'97 1 access is not valid [0xffffffff], removing mixer.
[17179599.132000] ali mixer 1 creating error.
``` However, my sound works fine, so if you have a similar message, it's probably not the problem.

If you go to System > Administration > Device manager,  you'll see a list of the hardware that Ubuntu recognizes. While it isn't in a very readable format, you might be able to glean some information about what Ubuntu thinks about your sound card.

---

### Post by macogw on 2006-08-24
One thing I've noticed with sound is that if you mute it before you shut down, when you turn it back on, the speakers tend not to work.  Restart with the sound turned on, and it'll work when it boots back up.  Just unmute before shutting down each time if you ever use mute.

---

