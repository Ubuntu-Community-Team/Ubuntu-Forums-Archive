---
title: "Launching VMare Server"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by singlewc on 2007-11-06
I am not sure exactly how I did it, but using the great posts in the archives, I was able to install Vmware Server in Ubuntu 7.10, to run win2k for those tricky apps that I need.

Anyway, the problem is not the VM, but in starting it up.

I have a root account, and my account on the machine. I admit to having gotten a bit lost during the install, but I am pretty sure I needed to be root in order to do it, or at least to do some of the hoops I jumped through.

The install created an icon in the applications section, which doesn't work, because in order to start VMware, I have to open a terminal, and 'sudo vmware' which then asks me for MY password, not the root password.... This confuses me on several levels. Why, if I am logged in as john, and I 'sudo' does it ask me for john's password? I thought that it would make need the root password, and execute as root??

More than that, this is hardly an elegant way to start the VM.  How can I get to where I can just use the icon in the applications list. Obviously, if I have to 'sudo' to use it, I cannot just click away.

Any help would be appreciated.

Thanks,

John

---

### Post by Scunizi on 2007-11-06
Your root password is your user password.  But it shouldn't be necessary to use it when starting VMWare server..  I don't.  My icon off the App menu works fine.  When installing I did have to "sudo ./<install file>" to get it to install.  You should not install from a "root" enabled account and then try to access it from your standard account.. That might be where your problem lies.  Uninstall using the root account then reinstall using your normal account.  You have to preface commands that require root privileged with sudo then use your user password to complete.

---

### Post by singlewc on 2007-11-06
> **Scunizi said:**
> Your root password is your user password.  But it shouldn't be necessary to use it when starting VMWare server..  I don't.  My icon off the App menu works fine.  When installing I did have to "sudo ./<install file>" to get it to install.  You should not install from a "root" enabled account and then try to access it from your standard account.. That might be where your problem lies.  Uninstall using the root account then reinstall using your normal account.  You have to preface commands that require root privileged with sudo then use your user password to complete.


Thanks. I never sudo'd as root. It always asks for my 'john' password, which is stupid, since I gave it when I logged into the system in the first place. Why does it even need me to 'sudo' when its me in the first place.

My root password is different than my user password. I changed it when I logged in the first time. What do you mean, 'my root password is my user password?" Now I am more confused <g>

I would be interested in knowing how it is that when I want to run it, I have to sudo to my own account and password. That makes no sense. I am no guru by any means, but still, I cannot fathom the how or the why. I am 'john' I logged in as 'john' and gave my password at the start of the session. In order to run this app, I have to give my password again? Obviously, I just don't get it :-)

I could never reinstall the server. I have no idea how I did it in the first place. I only followed whatever instructions were given, across three or four posts and web pages.....Jumped back three steps, and went through a lot of stuff I have no idea how to replicate. Besides, I don't know if that is the problem, as nothing was ever done under 'root'

Very strange, but thanks, and I will keep using the terminal till I am proficient enough to re-install <g> or have to reinstall unbuntu altogether.

Onward!

John

---

### Post by HermanAB on 2007-11-06
Go to wherever you VMs are, then change the owner and group to yourself.  From now on, you can run vmware as yourself.  For example, if the VMs are in /home/vmware then:

$ cd /home
$ sudo chown -R yourname:yourname vmware
$ vmware
La voila!

Cheers,

Herman

---

