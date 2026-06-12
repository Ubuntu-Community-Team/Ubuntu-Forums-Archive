---
title: "Where does an RPM go for more processing?"
date: 2006-02-06
forum: Absolute Beginner Talk
---

### Post by bingoldsby on 2006-02-06
I am trying to get a better version of VNC, which I have downloaded as an RPM. It is on the desktop, but Alien can't find it to convert it.

Where should it be put to get the process started?

I'm clueless - about a lot of linux things.

Thanks,

---

### Post by Klaidas on 2006-02-06
Does alien return any error messages?

PS: copy the file name, maybe you mistyped it :)

---

### Post by Perfect Storm on 2006-02-06
```
cd /where/you/saved/the/.RPM
sudo alien XXXXXXXX.rpm
sudo dpkg -i XXXXXXXX.deb

```

---

### Post by bingoldsby on 2006-02-06
Terminal returns this message:

brian@Brianlinux:~# sudo alien tightvnc-1.3dev7-1.i386.rpm
File "tightvnc-1.3dev7-1.i386.rpm" not found.
brian@Brianlinux:~#

===========================

And thanks for the change directory commnd. That sounds logical, now that I think of it.  However, where should the RPM actually go for alien or installers to find it withought having to manually change directories?

Thanks for the quick replies.

---

### Post by Perfect Storm on 2006-02-06
> And thanks for the change directory commnd. That sounds logical, now that I think of it. However, where should the RPM actually go for alien or installers to find it withought having to manually change directories?

I don't quiet understand what you mean :confused: 

An easier way:
```
sudo alien
```
Then drag the .rpm file into thte terminal so it says:

```

sudo alien /blah/blah/blah/XXXXXXX.rpm
```

---

### Post by bingoldsby on 2006-02-06
Yes the latter part worked. Thanks for showing me the shortcut.

What I meant (and I'm still on the Windows side of the big wall) is: what should I do when I'm downloading files (like this VNC .rpm, which I just did) so that they go to a logical place for installation?  Doesn't alien expect to find it somewhere so that its filename can just be specified after the "alien" command?

I'm way too new to even understand what I'm asking, I guess.

Thanks for the help.

---

### Post by carlosqueso on 2006-02-06
nope...when you download an RPM, they go to wherever firefox is set to download files, (usually your desktop by default).  Alien just looks AFAIK in whatever directory you're currently in, which when you open a terminal is your home directory.  If you want to just be able to use alien, you have to change firefox's default download location to your home directory instead of your desktop. (I think it's under Edit->Preferences).

---

### Post by bingoldsby on 2006-02-06
Thank you. I do get it.

And while we're here, I'm a little puzzled by the sudo - root - user(me) thing. I have tried to add icons to the desktop while logged in as me. Each time, I get an error thusly:

Error while moving.

"/usr/share/...sol.desktop" cannot be moved because you do not have permissions to change it or its parent folder.

So I added root to my password (or the other way around - I'm confused about that also) and when I log in as root, I can move the icons onto the desk top (from usr/share/applications which has lots of stuff I want to put on the desktop) but the desktop is a different one than that of which I get when logged in as me - the standard user.

Is there a guide to doing this kind of configuring?

Thanks again.  Little pieces at a time.

---

### Post by Sokraates on 2006-02-06
I guess there's a basic misunderstanding here.

First the basics: A user always has full access to his own home-folder (e.g. in your case /home/bingoldsby; **not **/home/sokraates and **neither** /home). 

All other folders and the files contained therein he may be able to view (e.g. take a look a repositories listed in /etc/sources.list or some icons in (/usr/share/pixmap), but you can **not** modify or delete those files.

For system-administration you have to become "root", since you need to access a bunch of folders. In Ubuntu there is no dedicated root-account, rather the command "sudo" is used to start an app with root-privileges. So 
```
sudo synaptic
``` will start synaptic with root-privileges (after entering your password) and you will be able to install software. You know this already, I guess.

Now for your problem: You tried to **move** fiels from /usr/share/... to your desktop. Moving a file means deleting it in the oldlocation and creating it anew in the new location. The problem is: you don't have permission to delete files anywhere but in your own home-folder. If you **copy** the file, everything will work just fine.

As for root: you've created a new root-account. So of course you have a different desktop. Best leave root-account be, unless you want to do some heavy maintanace in a graphical enviroment and are contious enough **not** to surf as root. By the way: root's home-folder is /root, not /home/root.

---

### Post by bartbes on 2006-02-06
But if you want to do it as root and you can do it in the terminal and need a lot of sudo's else just use ```
sudo -i
or
sudo -s (you can add -H as well to stay in the current dir)

```
It's better to copy or link them ```

copy:
cp *from to*
link:
ln *original link*

```

---

