---
title: "how do you make a fully customized fork of Ubuntu"
date: 2012-12-02
forum: Any Other OS
---

### Post by mythic97 on 2012-12-02
Yeah its in the title how do I start building an OS fork of Ubuntu?
I used some software but I want to make it a true Fork barely traceable back to Ubuntu 12.04 this just chooses packages and changes the desktop environment so how do I do this?
And how do I make a Desktop environment from source code?

OS name: dragon
Desktop environment: Blackbox fork
main goal: programming and usability 

please give me some info at least, I don't want sceptical reply's

---

### Post by viper250 on 2012-12-02
whether its ubuntu or another distro you need to download the linux core files and build from.
them this is how you fork out from a branch. otherwise you are doing a re spin off of another distro.
regardless if you heavily customize a distro for certain functions and needs that may be your distro but it may not be for everyone.
you need to carefully select the apps you are going to use and make the distro easy to use and navigate. 
keep this info in mind when you plan your distro
for example knoppix distros have a lot of useful software but can tend to be overwhelming to use. :(
and gentoo can be a nightmare to configure correctly. :confused:but when done right you have a wonderful machine.
ubuntu styles and their installers are easy to use and configure. :guitar:

---

### Post by Cheesehead on 2012-12-02
> **mythic97 said:**
> Yeah its in the title how do I start building an OS fork of Ubuntu?

- Download all of the source packages you want to change.
- Change the source code.
- Compile those changed sources.
- (Optional) Package those changes.
- Test those changes.
- (Optional) Distribute.

Which step do you need help with?

---

### Post by Chdslv on 2012-12-03
> **mythic97 said:**
> Yeah its in the title how do I start building an OS fork of Ubuntu?
I used some software but I want to make it a true Fork barely traceable back to Ubuntu 12.04 this just chooses packages and changes the desktop environment so how do I do this?
And how do I make a Desktop environment from source code?

OS name: dragon
Desktop environment: Blackbox fork
main goal: programming and usability 

please give me some info at least, I don't want sceptical reply's

Well, whether you download the mini.iso and build from that or download Ubuntu vanilla distro or some other distro, you get the same results--you have to change the branding anyway. If you are using another Ubuntu remix to make yours, you'd have to take away that's distro's branding, which would be a headache.

If you download the the vanilla Ubuntu and go from there, you'd have some of the applications, you'd want to install, so it'd be help. Whichever way, you cannot take away the Ubuntu branding and the legacy 100% out of it. It'd still have Ubuntu repos, for your new distro to update itself. Also, you have to find a way to not to break your distro, when someone upgrades.

Once, you have made your distro, you have to change these 3 files, /etc/issue, etc/issue.net and /etc/lsb-release, and if it is done with another Ubuntu remix, you might have to change at least one more file, if that developer had changed the grub supplier file.

Most times, you can leave /etc/issue and /etc/issue.net as it is, but /etc/lsb-release has to be changed for Grub to see your distro's name. Mind you, you still have Ubuntu parts, and all could never be thrown out. 

But, just changing /etc/lsb-release won't help, if you don't add at least one file to /usr/share/python-apt/templates. In that folder, you'd see a file named Ubuntu.info. You have to copy is and rename it to Dragon.info--copy and paste Ubuntu.info while you are gone there as root and rename it Dragon.info. The word in front of .info must be exactly the same as you had written in /etc/lsb-release, that is, if you've written dragon there, then it should be dragon, or if you've written Dragon, then it should be Dragon--its case sensitive.

You should also check  /etc/default/grub and if the line is GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
there's nothing to change there. if there is a another name, just delete that and copy the above line.

Now, what you do with adding or subtracting applications is entirely up to you, the new Dragon distro you get is already has the ability to update/upgrade.

If you have any Ubuntu remix - Mint, ZorinOs, Pinguy, SnowLinux,  or whatever, check those files, I mentioned above, and you might notice that some of them had changed only the /etc/lsb-release, and some had changed all the 3 files. And, there are some, who had changed the Grub-distributor's file.     

There are some list files to be changed, but I can't remember right now.

Have an excellent experimenting!

Good day!

PS: Simple test, change the /etc/las-release and add your-name copy of Ubuntu.info in the /usr/share/python-apt/templates of your vanilla Ubuntu 12.04 and update it. If it updates, you on your way and the vanilla Ubuntu had become your distro. do a 
sudo update-grub and reboot. You'd see your name -Dragon in the first window you see. ** It may take you less than 3 minutes.**

---

