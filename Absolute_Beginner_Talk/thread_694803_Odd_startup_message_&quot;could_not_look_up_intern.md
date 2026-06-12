---
title: "Odd startup message &quot;could not look up internet adress for name&quot;"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by revolutionaction on 2008-02-12
Hi, I recently had a problem with my $HOME/.dmrc file being ignored, got that all fixed up with the help of a nice member of these forums, but I still get this message directly after I sign in ""could not look up internet adress for josh. This will prevent Xfce from operating correctly. It may be possible to correct the problem by adding josh to the file /ect/hosts on your system."

I believe this is whats causing me to not be able to install some programs via the Terminal and add/remove (although aMSN installed successfully.) I've tryed all night trying to install the restricted codecs with various commands, and they worked to no avail. VLC gets corrupted during the 6 packet install in the add/remove. Is the start up problem the reason why my internet is kind of screwy? I can infact browse the internet and download a few things, but my use of it is somewhat limited.

I've found this thread where someone has pretty much 100% the same question as me, but I found the explanations a little hard to decipher. Is this saying I should reinstall Xubuntu??  [http://ubuntuforums.org/showthread.php?t=686355](http://ubuntuforums.org/showthread.php?t=686355)

---

### Post by dca on 2008-02-12
if you open the /etc/hosts file in an editor is there a 'josh' entry listed?
Navigate to it in nautilus, Places -> Computer and navigate to the file hosts in the /etc directory.  Right-click and select open w/ editor.  This way you're not su (root) and can't make any changes until you're ready.  Or you can hight-light and copy/paste it into reply...

---

### Post by revolutionaction on 2008-02-12
First of all, my /ect/hostname file contains 'josh'.  When I go to edit the /ect/hosts file to put in 

```
127.0.0.1 localhost
127.0.1.1 josh

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

it will not let me save it, says "write error, cannot save"

I'm thinking a reinstall is inevitable!

---

### Post by dca on 2008-02-12
That's why I had you navigate to it instead of opening an editor at CLI because I didn't want you to delete the entry...  Your hosts file looks just like mine...
Do the same thing w/ the /etc/resolv.conf file

---

### Post by dca on 2008-02-12
Read this one towards the bottom and see if it's similar to your problems ignoring the DE used:
 
[http://www.linuxquestions.org/questions/linux-newbie-8/could-not-look-up-internet-address-222777/:](http://www.linuxquestions.org/questions/linux-newbie-8/could-not-look-up-internet-address-222777/:)

---

### Post by revolutionaction on 2008-02-12
Sorry just had a little trouble following along, since I don't have nautilus, I have thunar not nautilus, Xubuntu, remember? : ]

Is there a way I can make myself able to edit the hosts file? also: I have another question. Where do all of the things that I type into the terminal go when I download them. It said they downloaded but nothing initialized after they downloaded for me to install them. Can I clean these files up because I think they may be creating a problem when I try to reinstall them, andddd where are the repositories handled exactally?? 

Thanks alot for your help ! 

new new linux noob : 0

---

### Post by revolutionaction on 2008-02-12
I think that actually is the problem, with the DNS server. I think I accidentally deleted something in there befor :S Now I just need to figuire out what to fill in there, 

Thanks a lot for everything. The Ubuntu community is the best community in the world!  : D

---

