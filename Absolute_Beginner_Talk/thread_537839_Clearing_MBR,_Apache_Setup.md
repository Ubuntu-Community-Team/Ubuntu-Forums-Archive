---
title: "Clearing MBR, Apache Setup"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by DR4545 on 2007-08-29
Hello, I had a couple questions.

- I was wondering if there's a way to clear out the MBR before reinstalling.  Having grub show a bunch of old OSes that have been erased whenever I boot can get annoying.

- Also, I am getting ready to install Apache.  I found a guide on how to do this if you *don't* install LAMP here: [http://www.howtoforge.org/perfect_setup_ubuntu_6.06_p6](http://www.howtoforge.org/perfect_setup_ubuntu_6.06_p6)

Is it easier to do this just by telling the initial installation to instal LAMP?  If so, what steps should I follow instead (perhaps link a guide?)  I'm pretty confident the router and everything are set up right, just need to get apache set up.  I'm also not sure which folder to actually store the .html files in.  Sorry if these seem like basic questions, I've been searching all over for guides but I wind up confused :(

I'm planning on using Ubuntu 6.06 LTS for my OS, but not dead-set on it if you have another recommendation.

Thanks for helping

---

### Post by jamvegan on 2007-08-29
If you're planning to do a clean install, that will clear out your list of old OSes.  That information is actually not stored in the MBR, it's stored in /boot/grub/menu.lst, so you could get rid of it at any time by editing that file and deleting or commenting out (with #) the lines related to the old OSes.  If you do a clean install, the file will be written anew, based solely on OSes that are detected during the install.

I did not install LAMP as part of my initial Ubuntu install.  I installed all of the components later via Synaptic, which was easy and resulted in no problems for me.  I think that installing Apache via Synaptic or apt would be your easiest option.  The guide that you link looks perfectly reasonable if you need all of that.  You said that you don't want LAMP.  Is it just MySQL that you don't want?  Because that guide gives you a pretty complete PHP install as well as Apache, and you're installing on Linux, so I guess you'd end up with LAP. :-)

---

### Post by DR4545 on 2007-08-29
I do want mysql and php, guess I wasn't clear about that.  The pop stuff I don't think I care about.

So you're saying since I had a couple installs before, and it asked to install the grub bootloader and I said yes it kept the old file, but otherwise it would delete it?

I had another question which I forgot in the OP.  If I want to grant myself root priveleges using the File Browser, is there a way to do that, or is it only possible inside the terminal?  (And I suppose I mean that for gedit)  Reason I ask is that I still feel awkward using vi, despite reading a couple guides that showed the basic functions.

---

### Post by jamvegan on 2007-08-29
> So you're saying since I had a couple installs before, and it asked to install the grub bootloader and I said yes it kept the old file, but otherwise it would delete it?

Hm.  No.  If you said to install the grub bootloader it should have completely replaced both the MBR *and* /boot/grub/menu.lst.  Are the old OSes that you're talking about old versions of Ubuntu?  If so, are there kernels corresponding to them in /boot with names like 'vmlinuz-2.6.20-15-generic'?  Anytime that you install a new kernel (for instance through the update manager), menu.lst is updated to include all kernel versions that you have in /boot.  And installing new kernels does not delete the old one(s).  So, if you have an Ubuntu system that you've been regularly updating for a while, you can end up with a lot of kernels (and a lot of entries in your grub menu).

> If I want to grant myself root priveleges using the File Browser, is there a way to do that, or is it only possible inside the terminal? (And I suppose I mean that for gedit)

Here's one way to deal with this:
1) Right-click on an empty part of the desktop.
2) Select 'Create Launcher...'
3) Leave the Type as Application
4) Give it a Name, like 'Root Gedit'
5) For Command enter 'gksu gedit'
6) Enter any Comment you want, or leave it blank
7) Click OK

Now you'll have an icon on your desktop that you can click to launch gedit with root privileges.  It will ask for your password when you start it up.

Apache configuration can be quite complicated, but there's not a lot that you *have* to do to get it going.  There is Ubuntu documentation that does a pretty good job of introducing various configuration options in the [Ubuntu Server Guide]("https://help.ubuntu.com/7.04/server/C/"), though some of it is out of date.  The [Apache documentation]("http://httpd.apache.org/docs/2.0/") is really good, though there's quite a lot of it.  The document root in a default Feisty install will be /var/www.  When you come up with other specific questions, ask them here, and someone will help you! :-)

---

