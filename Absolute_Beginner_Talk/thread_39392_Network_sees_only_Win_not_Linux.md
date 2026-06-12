---
title: "Network sees only Win not Linux"
date: 2005-06-04
forum: Absolute Beginner Talk
---

### Post by Olflo on 2005-06-04
Hello everyone,
I am happy with a brandnew Hoary install, which went very smooth on an AMD64.
I have a  Laptop running Windows and Ubuntu recognizes it straight away using WLAN. I am reading and writing Files both ways, just the way I want it.
But I cannot figure out why another elderly 220MhZ Desktop running SuSe Linux is nowhere to be found....this one is hooked up on the same hardware router/switch with his buddy running Ubuntu.
The Hardware is surely being recognized, Internet was instant too during installation...
I tried some of the stuff in
[http://ubuntuguide.org/#installsamba](http://ubuntuguide.org/#installsamba) 
but it didnt do any help.
Any ideas?

---

### Post by royg1234 on 2005-06-04
I'm getting this, too.  Desktop and laptop, both dual-booting XP and Ubuntu Hoary.  Ubuntu/XP networking works fine, but Ubuntu/Ubuntu doesn't work.

Laptop is wireless btw, if that makes a difference.

---

### Post by bonusiso on 2005-06-05
i have some problems like this but i can see same of the PCs on network. however i cant see all ??? 

AND &#304; WONDER THAT A LOT:  HOW CAN I CONNECT OTHER COMPUTERS ON TERMINAL?? \\:D/  \\:D/

---

### Post by lakcaj on 2005-06-05
For networking two unix machines together, I don't think anything beats ssh.  In a terminal, you can ssh into another machine (that is running the ssh daemon) and then all the commands you issue (until you log out) are being run on that machine.  You can also use scp to securely copy files back and forth between machines that are using ssh.

However, like both of you, I am completely _FLOORED_ by the fact that there are no good network discovery utilities for linux, other than the CLI ones such as nmap.  There is cheops, which I have played with, but it is very ugly and the UI is buggy.

Well, anyway, if you want to find all the machines on a particular network using the CLI, you can just do things like the following:

nmap -sP 192.168.0.*
nmap -sS 192.168.0.*

man nmap for more info.

---

### Post by Gtaylor on 2005-06-05
You can also add lines to your /etc/hosts file that'll let you call a name by some nickname rather than an IP address, like take my desktop, stimpy, for example:

In /etc/hosts
```

192.168.0.68 stimpy

```

And as a side-note, what do you mean by "can't see?", as in total unreachable and unresponsive to commands like 'ping', or doesn't show up on Network Neighborhood in Windows XP?

For Ubuntu->Ubuntu file transfers, consider using gFTP and selecting SSH2 from the protocol drop-down there. I've found this to be a great graphical way to swap files. You can also consider configuring Samba or NFS (see [http://ubuntuguide.org](http://ubuntuguide.org))

---

### Post by Olflo on 2005-06-07
Gtaylor,
cant see means there is no sign of the other linux desktop machine in any of the GUIs that I have found in Kubuntu for browsing the Network. I'm not much of a console hacker so i'd like to be able to access the network in some sort of browser or the like.
Later on it would be nice to be able to log in from one machine to the other but thats for the future. 
any help is appreciated

oh and lakcaj: I have no man page for nmap and the command returns

nmap -sP 192.168.0.*
bash: nmap: command not found

thats of little help

---

### Post by lakcaj on 2005-06-07
[QUOTE=Olflo]Gtaylor,
oh and lakcaj: I have no man page for nmap and the command returns

nmap -sP 192.168.0.*
bash: nmap: command not found

thats of little help[/QUOTE]


Are you kidding me?  :roll: 

"command not found" ... maybe you should use apt and INSTALL IT!

Sorry to come off a little harsh, but the "thats of little help" comment is a little much.  I'm not about to hold your hand.

---

### Post by Gtaylor on 2005-06-07
Use Synaptic to install the **nmap** package.

---

### Post by Olflo on 2005-06-09
Alright thank you,
i will try installing that package (nmap). 
I deliberately am posting to the newbie section, cause thats what i am: newbie to linux.
lakcaj:sorry,  no offense intended, I was talking about the command not about you when I wrote: thats of little help.
I will install, then try again and get back to you later.

---

### Post by Olflo on 2005-06-12
hi,
ive installed the nmap utility and scanned around. Luckily my ubuntu machine does see the other linux desktop, but not vice-versa ! 
nmap tells me the other host, lets call him linux is up and has a port open for ssh. I've tried to fiddle with that but there are lots of files to be edited and public and private keys to be exchanged, i dont really see through it all.
Is there a fairly fast and easy-to-go way to help me mount my home directory on linux as a folder on ubuntu? ubuntu doesnt have a floppy drive so i cant carry large public keys from one machine to the other. 
maybe using ssh is not so hard after all but can someone explain it to me from the start?

---

