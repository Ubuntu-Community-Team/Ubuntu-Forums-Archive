---
title: "rdesktop... cant get it to work =("
date: 2006-10-25
forum: Absolute Beginner Talk
---

### Post by XeroCurve on 2006-10-25
I have been reading and trying things for weeks now and havent been able to share a file or even see another computer over my network. I was trying to get"rdesktop" running to no avail. I am kind of at my wits end when it comes to networking ubuntu. Please any help would be great.

Running kubuntu (Dapper) on 3 machines.
192 network
static ips

I would be ecstatic if I cold just get a folder shared, but id also love to get rdesktop working.

I have checked my hosts, hosts.allow, hosts.deny and I think there correct.

I can ping the other machines but thats as far as I can seem to get.

HELP !

---

### Post by XeroCurve on 2006-10-25
Please...](*,)

---

### Post by dbott67 on 2006-10-25
These are for Gnome/Ubuntu, but you'll need to find the similar settings in kubuntu.

**_UPDATE:  Check here_**

[http://ubuntuguide.org/wiki/Dapper#Remote_Desktop_Sharing.2FDuplication_via_VNC](http://ubuntuguide.org/wiki/Dapper#Remote_Desktop_Sharing.2FDuplication_via_VNC) and 
[http://docs.kde.org/development/en/kdenetwork/krfb/krfb-configuration.html](http://docs.kde.org/development/en/kdenetwork/krfb/krfb-configuration.html)


For remote desktop, click on [B]SYSTEM > PREFERENCES > REMOTE DESKTOP
[/B]
**Check** *ALLOW OTHER USERS TO VIEW MY DESKTOP*
**Uncheck** *ASK YOU FOR CONFIRMATION*
**Check** *REQUIRE USER TO ENTER THIS PASSWORD*

Then from the remote computer, open a terminal & type:
```
vncviewer ip.address.of.remote
```

Also, make sure that you're not running a firewall (iptables/firestarter/etc.)

-Dave

---

### Post by XeroCurve on 2006-10-25
OK, once again I must gripe about the help. I appreciate the reply but it didnt help me at all. This is a "ABSOLUTE BEGINNER" forum, isnt it? I cant count how many times I have read the word EASY or JUST INSTALL whatever. Please, I beg of you! I am determined never to go back to windows but this is very hard to get used to. I am a beginner and I need beginner help. I have been working on windows machines for a long time and when you install something, you generally execute it and it works, now how well it works is another topic. It seems that very few things are like that in linux. I have been successful in installing kubuntu, ubuntu, and xubuntu and ive settled with kubuntu. I have installed all applicable plugins for browsers and got them working. So far I feel like im getting my feet wet, but the next thing I need is networking help

I need to share files between 3 machines all kubuntu (Dapper), and I need to have remote desktop working.

I cant get either thing working. If someone tells me "Just install" anything ill pull my hair out.

Ive fallen and I cant get up :D  please help me ! (remember beginner)

---

### Post by dbott67 on 2006-10-25
Take a deep breath... bitching & moaning isn't going to make anyone want to help.  Nowhere in your post do you mention 'beginner'.  When I reply to posts, I just click NEW POSTS; rarely do I ever pay attention to the "forum" (beginner vs. network vs. server, etc. --- if I can help, I post).  You seem to have been searching for answers & trying different things, so I assume you have some basic working knowledge.

Specific to my post, I never asked you to install anything.  I just posted how to do it in Ubuntu (Gnome) & then realized you were using Kubuntu (KDE), so I posted a link to the "HOWTO".

Okay... let's start at the beginning.

I'll make the assumption that your 3 computers have the following IP addresses:
192.168.1.1 - Computer 1
192.168.1.2 - Computer 2
192.168.1.3 - Computer 3

**_REMOTE DESKTOP_**

1. You mention that all computers are already networked and can ping each other.  To test, open a terminal and ping the IP address of the other computers. Press CTRL-C to stop pinging:
```
dbott@thedrake:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=127 time=0.648 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=127 time=0.564 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=127 time=0.568 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=127 time=0.584 ms

--- 192.168.1.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2997ms
rtt min/avg/max/mdev = 0.564/0.591/0.648/0.033 ms
```

```

dbott@thedrake:~$ ping 192.168.1.2
PING 192.168.1.2 (192.168.1.2) 56(84) bytes of data.
64 bytes from 192.168.1.2: icmp_seq=1 ttl=32 time=0.295 ms
64 bytes from 192.168.1.2: icmp_seq=2 ttl=32 time=0.226 ms
64 bytes from 192.168.1.2: icmp_seq=3 ttl=32 time=0.228 ms
64 bytes from 192.168.1.2: icmp_seq=4 ttl=32 time=0.230 ms

--- 192.168.1.2 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2999ms
rtt min/avg/max/mdev = 0.226/0.244/0.295/0.034 ms
```

```

dbott@thedrake:~$ ping 192.168.1.3
PING 192.168.1.3 (192.168.1.3) 56(84) bytes of data.
64 bytes from 192.168.1.3: icmp_seq=1 ttl=32 time=0.295 ms
64 bytes from 192.168.1.3: icmp_seq=2 ttl=32 time=0.226 ms
64 bytes from 192.168.1.3: icmp_seq=3 ttl=32 time=0.228 ms
64 bytes from 192.168.1.3: icmp_seq=4 ttl=32 time=0.230 ms

--- 192.168.1.3 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2999ms
rtt min/avg/max/mdev = 0.226/0.244/0.295/0.034 ms
```

If you get a response, then the computers can "see" each other.  You'll need to do this from each computer.

2. As posted in the link provided above on how to setup [REMOTE DESKTOP IN KUBUNTU]("http://ubuntuguide.org/wiki/Dapper#Remote_Desktop_Sharing.2FDuplication_via_VNC"), perform the following steps on any machine that you want to "share the desktop":
[B]
KUBUNTU (or KDE desktop) users:[/B]

    * K Menu -> System Settings -> Internet & Network -> Sharing
    * Desktop Sharing 

Access tab ->
Allow uninvited connections (Checked)
Allow uninvited connections to control the desktop (Checked)
Password: Specify the password

3. Suppose that you want to connect from COMPUTER 1 to COMPUTER 2.  On COMPUTER 1, open a terminal and type:
```
vncviewer 192.168.1.2
```

You should be prompted with a password field.  Enter the password that you specified in STEP 2.

4. Test & repeat for each of the other computers that you want to remote access to.
[B][U]
SHARING FILES[/U][/B]

*Keep in mind that I use GNOME, not KDE, but I believe that this option is the same:*

From [Vyruss]("http://www.ubuntuforums.org/showthread.php?t=196332&highlight=shared+folders")

In order to fully share a folder (read/write), right-click on it and select **Share folder**. Select **Share with: SMB**, type in a Name: and you're (almost) done.

Here's the tricky part everybody stumbles upon: this is not enough to make your shared folder writable!

You have to right-click on the folder again and select **Properties**, go to the **Permissions** tab and check **Read/Write** for **Group** and **Others**.

-Dave

---

### Post by XeroCurve on 2006-10-25
to dbott67,

I wasnt really bitching at you, sorry. I was just ranting. I love the whole idea and premise of linux and the community is overall great, it just seems that the beginner forum is filled with complex stuff and even though ive been around computers enough to figure a lot out the linux world is new to me and therefore frustrating and exciting at the same time. I will go over the things you mentioned and hopefully i can get it. Thanks a lot for the instructions.

:D

---

### Post by dbott67 on 2006-10-25
No worries... I know that the 'tone' of a message can easily be mis-interpreted (you can't see the smile on the face or the tongue-in-the-cheek).  Sometimes I post very detailed instructions and then the poster replies, ***"I'm not an idiot! I know how to re-configure the flux capacitor.  I compiled my own kernel for my washer & dryer and have been running Linux before Al Gore invented the internet!!"*** :)

I generally try to be as explicit as possible, as there may be others that read the forum that have zero experience and my posts are just as much for them, as it is for the original poster.

Good luck & keep us posted.

-Dave

---

### Post by dbott67 on 2006-10-25
I just installed KDE and to share a folder, open Konquerer and browse to the folder you want to share.  
- Right-click the folder
- Select **PROPERTIES**
- Click on the **SHARE** tab
- Click **CONFIGURE**
  - you should probably start with 'simple' just to see if it works.
- Click ADD and add the folder you want to share
- Click 'SHARE WITH SAMBA (MICROSOFT WINDOWS)'
- Provide a name for the share
- Select PUBLIC & WRITABLE (if desired)

See attached screen shot.

---

### Post by XeroCurve on 2006-10-25
For some reason when I go to the sharing tab and click configure it asks me for my password, then that window that you have on your example comes up grayed out, and I cant choose any options. I have noticed that a similar thing happens on the  "ZeroConf Service Discovery" window under system settings. Is there something that isnt running that needs to be?

---

### Post by XeroCurve on 2006-10-25
Insert AHA! moment now :D 

I thought this whole time I had samba installed, I guess I didnt. I went and installed samba:

Konsole:
[ sudo apt-get install samba smbfs ]

and all is wonderful in the land. I not only can browse folders but the rdesktop works now. I am guessing there is a dependency I was missing :-k , whatever it works now. Thanks so much for the assistance.

---

### Post by dbott67 on 2006-10-25
Glad to hear all is well! :)

-Dave

---

### Post by zek725 on 2006-11-15
at first, without configuring the Windows firewall (with **Remote Desktop** not yet checked), ```
ERROR: connect: Connection timed out
```

By checking that box (which i believe should open that Remote Desktop port:3389), ```
ERROR: connect: Connection refused
```

How do I fix this? I'm using Xubuntu Edgy; connecting to Windows XP.

---

### Post by dbott67 on 2006-11-15
Which program are you using to connect to the Windows computer, "VNC viewer" or "Terminal Services Client"?

You should be using the TSC and try connecting using RDP protocol.  The RDP protocol uses port 3389, while VNC uses 5900.

My recommendation is to **disable the Windows firewall completely** while you are testing connectivity.  If you can connect, you know that this is the problem.  Once you've got everything working, then try turning on the firewall and testing again.

Also, make sure that you have "turned on" Remote Desktop in Windows (it requires XP Pro).  If you're not using XP Pro, you'll need to install some variant of VNC (UltraVNC, RealVNC, TightVNC, etc.) and then connect using the VNC protocol (5900).  You'll also need to adjust the Windows firewall.

-Dave

---

