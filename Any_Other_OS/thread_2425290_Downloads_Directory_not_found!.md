---
title: "Downloads Directory not found!"
date: 2019-08-23
forum: Any Other OS
---

### Post by hanna-bethell on 2019-08-23
Hello all, very inexperienced Linux user here (using an Asus chromebook):
I'm trying to **launch an installation (Pycharm) from my Downloads folder **(trying to get started with some Python practice!) At the same time, I'm trying to figure out Linux. So far, I've opened a terminal and learned/practiced several commands while using advice i've read online, but I can't seem to get anywhere! I've tried:
**a)**
cd ~/Downloads
and received 'No such file or directory exists'

**b)**
So I've pwd and I know that i'm in the directory->  home/[my user name] 

**c) **I tried "ls -la" to see if it's just hidden, but I just see
 *total 16**drwxr-xr-x 1 hannabethell hannabethell   90 Aug 23 09:37 .*
*drwxr-xr-x 1 root         root           24 Aug 22 12:28 ..*
*-rw-r--r-- 1 hannabethell hannabethell  220 Aug 22 12:28 .bash_logout*
*-rw-r--r-- 1 hannabethell hannabethell 3526 Aug 22 12:28 .bashrc*
*drwxr-xr-x 1 hannabethell hannabethell   62 Aug 22 12:28 .config*
*-rw-r--r-- 1 hannabethell hannabethell  675 Aug 22 12:28 .profile*
[I]-rw------- 1 hannabethell hannabethell  104 Aug 23 09:37 .Xauthority

[/I]**Can you advise?  Thanks for your patience, etc. **:grin:

---

### Post by yancek on 2019-08-23
The cd command you posted should have taken you to the Downloads directory for that user and the ls -la command should have output any and all files in that directory.  Interesting that only hidden files show since all directories/files should show.   Is this a new install?  Were you ever able to access the Downloads directory and did you have all the standard directories/files in your /home/user directory?  If not, the installation was probably not successful.  Where did you download PyCharm, what site?

---

### Post by fragglebliss on 2019-08-23
I suspect you've probably (accidentally) removed your Downloads directory.

---

### Post by hanna-bethell on 2019-08-23
> **yancek said:**
> The cd command you posted should have taken you to the Downloads directory for that user and the ls -la command should have output any and all files in that directory.  Interesting that only hidden files show since all directories/files should show.   Is this a new install?  Were you ever able to access the Downloads directory and did you have all the standard directories/files in your /home/user directory?  If not, the installation was probably not successful.  Where did you download PyCharm, what site?

It is a new install of Linux and a new download of Pycharm. So far I haven't been able to access the Downloads directory via Linux, but I can access it in the usual Google Chrome way (through a folder--does that make sense?)

In my home/user directory I have: recent, audio, images, videos, my files. Inside my files, i have downloads, linux files, and play files.

I downloaded Pycharm from jetbrains.com..**it's possible the installation wasn't successful, but then why don't any of my other downloaded files show up with the original command?**

---

### Post by hanna-bethell on 2019-08-23
You might be right that I removed or transfer it, but I can still access the files through my Chrome directory...

---

### Post by fragglebliss on 2019-08-23
> **hanna-bethell said:**
> You might be right that I removed or transfer it, but I can still access the files through my Chrome directory...

Even if you've removed the directory, they'll probably still show up in your browser until you clear the Downloads from inside the browser. But just because they are visible in your Downloads history in the browser, it does not mean the ~/Downloads is actually still there.

---

### Post by hanna-bethell on 2019-08-23
> **fragglebliss said:**
> Even if you've removed the directory, they'll probably still show up in your browser until you clear the Downloads from inside the browser. But just because they are visible in your Downloads history in the browser, it does not mean the ~/Downloads is actually still there.

I don't quite understand your reply--I'm accessing the downloads _in_ my directory just fine (not in the browser):confused:, the trouble is I can't seem to get access in Linux.

---

### Post by Holger_Gehrke on 2019-08-23
You mention that you're using a chromebook. Are you using Ubuntu inside [crouton]("https://github.com/dnschneid/crouton") ? If so, you are inside a chroot environment when using Ubuntu and '~/Downloads' in Ubuntu and Downloads in ChromeOS are not necessarily the same ...

Holger

---

### Post by hanna-bethell on 2019-08-23
> **Holger_Gehrke said:**
> You mention that you're using a chromebook. Are you using Ubuntu inside [crouton]("https://github.com/dnschneid/crouton") ? If so, you are inside a chroot environment when using Ubuntu and '~/Downloads' in Ubuntu and Downloads in ChromeOS are not necessarily the same ...

Holger

Thanks for the reply (and thanks everybody above).

To my knowledge, I'm _not_ using Ubuntu inside crouton (to my understanding crouton is an extension you can download to let you use Linux and ChromeOS simultaneously??)
For the record, I'm not using Ubuntu--my Asus chrome had Linux that I just needed to switch on. 

What you say here about Downloads in Linux and Downloads in ChromeOS is kind of blowing my mind, but would help explain why my commands aren't working. Can you elaborate? How do I make it so Linux can 'name' files in my Downloads in ChromeOS?

---

### Post by ajgreeny on 2019-08-23
In a terminal run command ```
sudo updatedb && locate Downloads
```
That may show us where the Downloads directory now resides, assuming you did not totally remove it.

---

### Post by Holger_Gehrke on 2019-08-23
> **hanna-bethell said:**
> 

To my knowledge, I'm _not_ using Ubuntu inside crouton (to my understanding crouton is an extension you can download to let you use Linux and ChromeOS simultaneously??)
For the record, I'm not using Ubuntu--my Asus chrome had Linux that I just needed to switch on. 

What you say here about Downloads in Linux and Downloads in ChromeOS is kind of blowing my mind, but would help explain why my commands aren't working. Can you elaborate? How do I make it so Linux can 'name' files in my Downloads in ChromeOS?

If you're booting directly into Linux without crouton then my idea is obviously wrong. ChromeOS is an Operating System that uses the Linux kernel but has a completely different userland that is geared towards using the browser and web-apps, making the machine almost useless without a working internet connection. crouton sets up a chroot (changed root directory) and installs a GNU/Linux userland into that. Without further trickery it's quite difficult to access data outside the 'new' root-directory from programs running inside that "cage".

You might want to check in your browser settings where your downloads actually go ('Hamburger'-menu, Settings, "Show advanced settings" at the bottom of the page if you can't see a setting for "Downloads").

Holger

---

### Post by TheFu on 2019-08-23
Chromebooks don't run a standard Linux.  You'll need to visit specific forums for ChromeOS and using linux to get most help.

Of course, you could have taken extreme steps and wiped ChromeOS from the system, opened the case and broke the write-protection of the firmware, loaded new firmware that would allow non-ChromeOS operating systems to be installed, then installed some version of Ubuntu Desktop onto the device.  If this is the situation, people here can help.

I've had a few Chromebooks over the years, but never had any with the newer run-linux-applications capability.  I've used Crouton for a few months before being frustrated with the limitations (there are many) and doing what the paragraph above (write-protect, new firmware, load a real Linux OS) says. I was mostly happy with using a normal Linux distro on my chromebooks.  The only real problem I experienced was the terrible keyboards missing about 5 keys and that the keyboards wear out too fast.  Replacing a keyboard on a chromebook is like brain surgery.

As for the other things, ~/Downloads is just a directory.  If it isn't there, MAKE IT!  If you need some file that doesn't exist, MAKE IT.  Also, don't forget that Linux is case-sensitive, so 
```
~/Downloads
~/downloads
~/DownloadS
```
are all different.

I know nothing about python beyond the big picture stuff that knowing many other scripting languages has provided.

---

### Post by him610 on 2019-08-23
hanna-bethell and all responders,

I am a little late getting into this discussion, but I have a question concerning your chromebook. Is your Asus chromebook one of the recent models that can also run android applications?

---

### Post by TheFu on 2019-08-23
They use something called Crostini [https://www.zdnet.com/article/linux-comes-to-chromebooks/](https://www.zdnet.com/article/linux-comes-to-chromebooks/)
> How? Well that's a good question. Project Crostini will be bringing Linux VMs to Chrome OS using Linux's built-in Kernel-based Virtual Machine (KVM). It appears these VMs will run within containers. This should ensure that Chrome OS, which is known for its security, will continue to be secure. These Linux distributions will be run in sandboxes at two removes from Chrome OS's base operating system.

That's a bunch of buzzwords that don't really say what they are doing clearly.  I'd guess, this is the plan:
```
ChromeOS
&#9492;&#9472;&#9472; KVM-VM
    &#9500;&#9472;&#9472; linux-app1
    &#9500;&#9472;&#9472; linux-app2
    &#9492;&#9472;&#9472; linux-app3

```
Each app would run inside a separate container.

That means any directories used by an Linux application, linux-app1, couldn't be accessed by any other Linux application, linux-app2/3. That is one of the key reasons to use a Container, compartmentalization. Further, if these Containers are being run inside a KVM virtual machine, then the hostOS, ChromeOS, wouldn't have access to anything inside the KVM VM and similarly, the KVM VM wouldn't have access to anything in the base ChromeOS area.  KVM is a heavier form of compartmentalization that has been around about 15 yrs now.

KVM is a little heavy on a chromebook with only 4G of RAM.  I've run it, but on a 2G Celeron, it wasn't a little tight.  On a 4G Core i3 chromebook, it was fine for limited use. I used it only for servers - no GUI for the VMs.  Google did all this to be certain that the base ChromeOS security wasn't at risk.  ChromeOS is probably the most secure OS with networking available today and for the last 8 yrs or so.  The OS and hardware are tightly coupled.

---

### Post by him610 on 2019-08-23
> They use something called Crostini [https://www.zdnet.com/article/linux-...o-chromebooks/](https://www.zdnet.com/article/linux-...o-chromebooks/)
At the bottom the that link, it also states these requirements...
> To run the Linux VM in a Chrome OS container, you currently must:

Have a Pixelbook
Be on the Dev Channel
Enable the experimental #enable-cros-container flag
Open up a crosh terminal by pressing ctrl+alt+t
Run the following two commands:
vmc start dev
run_container.sh -container_name=stretch -user=<username> -shell

I have a recent Asus C302CA-DHM4 Chromebook, but I have not pursued using any Linux capabilities with it as I have several other machines with Xubuntu installed; however, I am quite satisfied with the capability of running some Android applications on it.

---

### Post by hanna-bethell on 2019-08-26
> **Holger_Gehrke said:**
> If you're booting directly into Linux without crouton then my idea is obviously wrong. ChromeOS is an Operating System that uses the Linux kernel but has a completely different userland that is geared towards using the browser and web-apps, making the machine almost useless without a working internet connection. crouton sets up a chroot (changed root directory) and installs a GNU/Linux userland into that. Without further trickery it's quite difficult to access data outside the 'new' root-directory from programs running inside that "cage".

You might want to check in your browser settings where your downloads actually go ('Hamburger'-menu, Settings, "Show advanced settings" at the bottom of the page if you can't see a setting for "Downloads").

Holger

[B]To the first paragraph, do you mean if I had crouton, or do you mean my system as it is now ('Without further trickery it's quite difficult to access data outside the 'new' root-directory from programs running inside that 'cage')?

Checked my browser settings! It's as I thought... Downloads are located inside of 'My Files'.
[/B]

---

### Post by hanna-bethell on 2019-08-26
> **him610 said:**
> hanna-bethell and all responders,

I am a little late getting into this discussion, but I have a question concerning your chromebook. Is your Asus chromebook one of the recent models that can also run android applications?

**&#8203;Yes, it is!**

---

### Post by coffeecat on 2019-08-26
@hanna-bethell, I think it's been established that you are running Chrome OS, not Ubuntu, so I've moved this thread to the Any Other OS sub-forum and added the ChromeOS prefix to your thread title.

Our focus on ubuntuforums is the Ubuntu family of operating systems, so questions about ChromeOS do not belong in New to Ubuntu or any of the other Ubuntu sections. Nevertheless, you are very welcome to post questions about ChromeOS in this section. That being said, you may find that a forum dedicated to ChromeOS may be useful to you. It's important to remember that although ChromeOS has a Linux kernel, ChromeOS as an operating system is a very different animal from Ubuntu, or other distros often loosely referred to as "Linux", such as Red Hat, Fedora, openSuse and so on.

Best of luck resolving the issue with which you started this thread, and if you ever decide to try Ubuntu on a suitable machine, do please make use of the Ubuntu sections of the forum here.

Cheers!

---

