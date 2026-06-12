---
title: "Ubuntu &quot;Gutsy&quot; in VMPlayer"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by draceena on 2007-12-22
Hi!

I am a totally new user to Ubuntu but certainly not new to computers and operating systems. I've worked in mainframe and servers and trained in Unix with a smattering of Linux, though it's been over ten years since I've mucked about with any of that.

After hearing about Ubuntu, I was interested in trying it out but am still unsure if I want to pull the plug on WinXP just yet.

I decided that it would be best for me to try Ubuntu in a Virtual Machine Environment as the husband is mostly clueless about the inner workings of dual booting and such and I was worried about accidently mucking up my XP system with the Live CD.

As such, I downloaded VMPlayer and an image of Ubuntu Gutsy Gibbon hosted on the VMWare site. So far, I've had Gutsy up and running, tried the games it had pre-installed and had a look at some of the other programs like Gimp which were also pre-installed.

The only problems I've had so far, I think have to do with VMPlayer more than Ubuntu but was hoping someone here might know the solution to my 2 questions.

Firstly, I was wanting to try surfing the net from Ubuntu but for some reason I can't seem to connect properly. I have High Speed Cable (not wireless) and when I activated DHCP through the Network function in Ubuntu, it seemed like it connected, and when I start Firefox in Ubuntu, the modem flashes like it's trying to connect but thats as far as it gets, the Firefox page says it can't connect.

Secondly, and possibly related, I was wanting to try copying some files from my computer to the Ubuntu or at least navigating from the Ubuntu to files on my computer to open them but I cannot seem to get that connection to work either.

Am I just barking up the wrong tree to have VMPlayer and a pre-built Image of Ubuntu? Would running a LiveCD offer the internet and opening of XP files?

So far I am liking Ubuntu but wan to play-test more before jumping in the deep end and possibly drowning.

---

### Post by Nano Geek on 2007-12-23
If I were you, I'd try the live-cd. You'll be able to access your Windows partition easier than you can in VMPlayer, and it should be able to connect to a network connection.

I hope you enjoy using Ubuntu. :)

---

### Post by draceena on 2007-12-24
Thanks for the reply!

I have just finished downloading the CD iso and will be burning it in the next few days. 

If I can give a suggestion to the makers of Ubuntu, I would love to see them host the file on a torrent rather than a dirrect download.

I hope everyone has a happy holiday and a error free ubuntu :KS

---

### Post by scxtt on 2007-12-24
there are torrents of ubuntu ... every release of ubuntu i've ever d/l'd has come off a torrent ...

as for the VMware Player aspect, i've not used Player in Windows and i've never used someone else's pre-built VM,  but i'm guessing your network problems come from a lack of a VMware network device, be it either Bridged or NAT ...

in XP, what does **ipconfig** return?

here's an example from a box @ work w/ VMware Server installed:
```
Ethernet adapter VMware Network Adapter VMnet8:

        Connection-specific DNS Suffix  . :
        IP Address. . . . . . . . . . . . : 192.168.12.1
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . :

Ethernet adapter VMware Network Adapter VMnet1:

        Connection-specific DNS Suffix  . :
        IP Address. . . . . . . . . . . . : 192.168.199.1
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . :
```those 2 devices are available for NAT connections, tho i generally used Bridged myself.

---

### Post by draceena on 2007-12-28
Still not wanting to mess up my system but wanting to get a fuller Ubuntu experience, I downloaded Virtual Box and then installed Gutsy Gibbon on it. Everything worked right off the bat. I have sound, internet and CD access!

I'm really liking what I am seeing and have only one small question. The Virtual Box help suggests I can make a Folder shared so that I can access the folder in windows but then start up my Virtual Ubuntu and accesss the folder as well

I've made the folder, named Shared and placed it in the Virtual Box folder (where the virtual hard drive is), but can't for the life of me connect to it. I open the terminal and issue the mount commant and it returns to me that I need to be in root.

I use the "cd" command to try and navigate to root but that gets me no where, and I'm definately stumped. Anyone have any clues to what I can do to access this Shared folder from within Ubuntu running on Virtual Box?

:confused:

---

### Post by dcstar on 2007-12-28
> **draceena said:**
> ........
I've made the folder, named Shared and placed it in the Virtual Box folder (where the virtual hard drive is), but can't for the life of me connect to it. I open the terminal and issue the mount commant and it returns to me that I need to be in root.
.........:

No, you need to **be** root:

```
sudo mount -a
```

---

### Post by The Cog on 2007-12-28
root is also the username of the system administrator. This should explain
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by draceena on 2007-12-28
Ahhh *slap forhead*

Boy I feel dumb, Sudo! of course!

Thanks soooo much. :D

---

