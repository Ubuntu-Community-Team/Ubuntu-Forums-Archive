---
title: "Pacman Issues"
date: 2008-05-17
forum: Arch and derivatives
---

### Post by jjte on 2008-05-17
Earlier today, I decided to jump into Arch, it was relatively easy to set up, even wireless went without a hitch, pacman, however, is proving itself to be a big problem.

First off, /etc/pacman.d/mirrorlist doesn't exist, I even reinstalled Arch incase I had screwed something up on my original install, still, I have no mirrorlist file.
In both installs, I specified the mirror I wanted in the installer.

When I run ```
pacman -Syy
``` it hangs at ```
::Synchronizing package databases
``` and eventually outputs ```
error: failed retrieving file 'core.db.tar.gz' from mirror.pacific.net.au : Connection timed out
error: failed to synchronize core: Connection timed out
```.

I can ping a variety of sites, including the mirror pacman is trying to connect to.

Any help would be much appreciated.

---

### Post by MONODA on 2008-05-17
try selecting a different mirror and putting it at the top in /etc/pacman.d/mirrorlist. You can also use the rankmirrors script to rank the mirrors by response time.
EDIT: remember to do a pacman -Syy after changing your mirrors

---

### Post by jjte on 2008-05-17
```
pacman -Syy
``` hangs, and I don't know where exactly I would change the mirror, considering I have no /etc/pacman.d/mirrorlist , and rankmirrors requires python, which doesn't come on the ISO, and I cant install.

---

### Post by MONODA on 2008-05-17
Oh I didnt know that you are on a fresh installation, in that case, follow the beginners guide on the arch wiki.

---

### Post by jjte on 2008-05-17
I'll take that as honest help, although it really does frustrate me when people tell me too look through a guide which has no help for my problem.
I have looked through the beginners guide over and over agian, there is nothing in there about pacman hanging, or a lack of a mirrorlist file.

---

### Post by MONODA on 2008-05-17
I will give you my /etc/pacman.d/mirrorlist file and my /etc/pacman.conf but keep in mind that in order to get a fully functioning system you should follow the beginners guide closely from beginning to end, there is a lot of good stuff in there. Anyway here is /etc/pacman.d/mirrorlist:[http://pastebin.com/m5fba9bf5](http://pastebin.com/m5fba9bf5) and /etc/pacman.conf: [http://pastebin.com/d7e9b08f3](http://pastebin.com/d7e9b08f3) keeo in mind that this should just be a guideline as to what your files should look like.

---

### Post by jjte on 2008-05-17
Thanks for your files, although I won't use them at this point, I'll try and get mine working first.

I understand you reccommending the Beginners guide, but all the advice it gives is pointless if you don't have the files referenced.

I have made a little progress by uncommenting ```
XferCommand = /usr/bin/wget --passive-ftp -c -O %o %u
``` but it seems that arch is resolving the mirror to the IP 1.0.0.0, then it times out.

---

### Post by MONODA on 2008-05-17
srry I dont know what to do, but considering that you havent done much so far, wouldnt it be easier to just reinstall? I had to reinstall a few times before I finally got everything right.

---

### Post by jjte on 2008-05-17
When I reinstall, which I have done, I am at the exact state I was in in the original post, internet working, but no Pacman/

---

### Post by MONODA on 2008-05-17
even immediatly after a fresh installation? make sure that in /etc/pacman.conf, the mirrorlist chosen is /etc/pacman.d/mirrorlist. so it should look like:
> [core]
# Add your preferred servers here, they will be used first
Include = /etc/pacman.d/mirrorlist

[extra]
# Add your preferred servers here, they will be used first
Include = /etc/pacman.d/mirrorlist

[community]
# Add your preferred servers here, they will be used first
Include = /etc/pacman.d/mirrorlist

---

### Post by jjte on 2008-05-17
Yep, that's what my /etc/pacman.conf looks like, but no /etc/pacman.d/mirrorlist.

It looks like I have seperate mirrorlists for each repository, Core, unstable, untested, community etc.

---

### Post by MONODA on 2008-05-17
yes that is how it was a while ago but recently they have changed it to have the entries in /etc/pacman.conf refer to /etc/pacman.d/mirrorlist . You should try and copy mine and see if that works.

---

### Post by jjte on 2008-05-17
Due to pacman not working, I'm unable to get a web browser working to copy your one.

Is it possible I've gone and downloaded an old version? I just used the torrent link on the "Get Arch" page.
My pacman.conf file refers to /etc/pacman.d/mirrorlist, but mirrorlist doesn't exist...

Edit: "Archlinux-i686-2007.08-2.core.iso" is the file name of the ISO I burnt.

---

### Post by MONODA on 2008-05-17
Links is supposed to come with arch so you can use that. If it is not available, download the RC of archlinux 2008, that is what I used. good luck

---

### Post by jjte on 2008-05-17
Thanks for the help, a user on the Arch forums told me to get the RC iso too, I'm halfway finished the download now.

Because of all this rolling release stuff, is this really a testing version?

---

### Post by MONODA on 2008-05-17
no, only the installation script (which is almost exactly like the old one) and the live cd part are considered RC.
EDIT: I the packages are just a more recent version which you would have recieved if you had used the 2007 disk and upgraded from there.

---

### Post by jjte on 2008-05-17
I've just installed using the newer ISO, and while I now have a /etc/pacman.d/mirrorlist, it still hangs and times out.

---

### Post by MONODA on 2008-05-17
make sure that in /etc/pacman.conf, the mirrorlist you want is refered to like in my example before.

---

### Post by odiseo77 on 2008-05-17
> **jjte said:**
> I've just installed using the newer ISO, and while I now have a /etc/pacman.d/mirrorlist, it still hangs and times out.

Did you uncomment the servers you want to use in /etc/pacman.d/mirrorlist ? I don't see other reason for pacman to time out (unless you have some problem with your network).

---

### Post by jjte on 2008-05-17
The server I selected in setp is uncommented, and I can ping it.

The same problem happens with any server.

---

### Post by MONODA on 2008-05-18
ok first I suggest that you ask around on the arch linux forums, it is great. second, what does pacman -Sy give you?

---

### Post by phil90 on 2008-06-03
Hello


I don't know what ISO you are using to install Arch but when I used  the 2008-04 I had the same problem.  When I use the 2008-03  Iso I don't have that problem.

---

### Post by crimesaucer on 2008-06-03
This is a bit older of an Arch guide that I used when I installed Archlinux-i686-2007.08-2.core.iso: [http://www.raiden.net/?cat=2&aid=276&pid=7](http://www.raiden.net/?cat=2&aid=276&pid=7)

This page 7 has details about the pacman.d and the server list. Also, read the notes that pacman will print out for you, it usually has all of the new details of any changes for the .conf files that you will have to make.

Read the whole guide (with pictures), and make sure you did all of your conf files correctly.

---

### Post by skip mcshwang on 2008-07-02
Did you find the answer to this? I have the same problem.

Followed the Beginners Guide exactly but pacman says "Connection timed out" no matter which mirror I choose.

---

### Post by fwojciec on 2008-07-02
> **skip mcshwang said:**
> Did you find the answer to this? I have the same problem.

Followed the Beginners Guide exactly but pacman says "Connection timed out" no matter which mirror I choose.

Do you have a working network connection?  Can you ping google, for example?

---

### Post by skip mcshwang on 2008-07-02
I can ping google and the mirrors.

---

### Post by Dr Small on 2008-07-02
Sorry, I haven't read the entire thread. But have you tried:
```
pacman -Sy
```

??

---

### Post by skip mcshwang on 2008-07-03
Dr Small, that's where I got snagged in the beginners guide, it says to update your system by typing pacman -Sy. It wouldn't connect so I tried skipping that part and installing libgl, xorg etc. but it says

```
error 'libgl': not found in sync db
```

---

### Post by YodaMstr on 2008-07-05
The first time I installed Arch, I remembered getting hung up on pacman.  I'm not entirely sure if it's the same thing being referred to here, but I remember it had something to do with how I was following the beginner's guide.  The guide's been updated since then, but try updating pacman using the archlinux.org server.  The guide had me set my mirrorlist and then run a full-system update, but the version of pacman I had was outdated and didn't refer to /etc/pacman.d/mirrorlist.  I don't see how this would be a problem on a release-candidate version, but I figured I'd mention it to see if it helps.

---

### Post by jjte on 2008-07-07
I got it working a while ago, and forgot to update this post.
Turns out that in /etc/rc.conf the default gateway was set to 192.168.0.1 when it needed to be set to 192.168.1.1.

---

### Post by skip mcshwang on 2008-07-10
jjte, you're right on the money, the problem was with the gateway!

Thanks everyone for your help!

---

### Post by LookTJ on 2008-07-11
> **jjte said:**
> I got it working a while ago, and forgot to update this post.
Turns out that in /etc/rc.conf the default gateway was set to 192.168.0.1 when it needed to be set to 192.168.1.1.just for your information, the gateway doesn't necessary need to be set. That is, only if you use DHCP. :)

---

### Post by curly_ on 2008-08-18
I had an issue very similar, and to solve it I used the DNS from my ISP, rather than my network one, if that makes sense.

---

