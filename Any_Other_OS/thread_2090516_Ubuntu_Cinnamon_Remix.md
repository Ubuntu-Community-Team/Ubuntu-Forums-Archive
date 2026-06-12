---
title: "Ubuntu Cinnamon Remix"
date: 2012-12-02
forum: Any Other OS
---

### Post by exploder on 2012-12-02
Just happened across this today.:)

[http://news.softpedia.com/news/Introducing-Ubuntu-Cinnamon-Remix-311264.shtml](http://news.softpedia.com/news/Introducing-Ubuntu-Cinnamon-Remix-311264.shtml)

---

### Post by mythic97 on 2012-12-02
Looks good but i think 12.04 is better, still great for getting new people into Ubuntu

---

### Post by viper250 on 2012-12-02
> **mythic97 said:**
> Looks good but i think 12.04 is better, still great for getting new people into Ubuntu

i agree getting them away from windows and mac is even better

---

### Post by Chdslv on 2012-12-03
Add;
deb [http://packages.linuxmint.com](http://packages.linuxmint.com) nadia main upstream import
 deb-src [http://packages.linuxmint.com](http://packages.linuxmint.com) nadia main upstream import

to your /etc/apt/sources.list and update. Then,
sudo apt-get install cinnamon, log out and choose Cinnamon.
You'd have a session with the newest; cinnamon-1.6.7+nadia

You'd have your own Ubuntu-Cinnamon Remix:)

---

### Post by exploder on 2012-12-03
I just thought it was cool that someone took the time to make this. It retains the Ubuntu specific features and has Cinnamon as the default desktop environment. Kind of nice for Ubuntu fans that would like a classic desktop out of the box. Using the LTS was pretty nice too.

---

### Post by ojdon on 2012-12-03
Why is this spin needed? Can't people find their own wallpapers and add the cinnamon PPA themselves? Doesn't require that much searching on how to do it. =\

---

### Post by Uncle Spellbinder on 2012-12-03
> **ojdon said:**
> Why is this spin needed? Can't people find their own wallpapers and add the cinnamon PPA themselves? Doesn't require that much searching on how to do it. =\

Why not? Those who want to do as you suggest are free to do so. Those who are distro hoppers/testers might like the idea of everything ready-to-go upon install without having to do searching and/or installing other stuff. There are many distros based on Arch, Gentoo, Debian, Fedora and others. Why not more Ubuntu based distros?. I say, the more the merrier. The beauty of Linux...Choice.


Here's their Sourceforge page: [http://sourceforge.net/projects/cinnamon-remix/](http://sourceforge.net/projects/cinnamon-remix/)


[SIZE="1"][COLOR="White"].[/COLOR][/SIZE]

---

### Post by mamamia88 on 2012-12-03
how many freaking remixes do we need people?   it's called mint people.    they are the developers of cinnamon and use ubuntu as a base so this is kind of redundant

---

### Post by Uncle Spellbinder on 2012-12-03
> **mamamia88 said:**
> how many freaking remixes do we need people?   it's called mint people.    they are the developers of cinnamon and use ubuntu as a base so this is kind of redundant

How many SID remixes do we need? How many Fedora remixes do we need? How many of any of the main distro remixes do we need. Nearly all distros are based on another parent distro (Red Hat, Fedora, SuSE, Debian, Arch, Slackware...). Hell, Ubuntu itself is a Debian "Remix". And NO. This is NOT Mint. Other than the Cinnamon DE, there are no Mint-specefic things that I can see. Especially that annoying Mint Update. This is Ubuntu 12.04 with Cinnamon. 

No need to use it or bash it. Linux is about choice. You choose not to appreciate it. Great.


[COLOR="White"][SIZE="1"].[/SIZE][/COLOR]

---

### Post by exploder on 2012-12-03
Well put Uncle Spellbinder! :)

---

### Post by wlake on 2012-12-06
Well, I have to say I like it. It seems a bit lighter in memory useage than LinuxMint 14 and may be quicker. Some things I noticed:

1. The installer was to me a bit unusual when it came to partitions. I did not use the installer on the desktop and instead started ubiquity from a terminal.
2. The weather applet has problems when trying to change the location. This seems to be a general problem. I installed dconf-tools and with dconf-editor was able to change the location.
3. When installing, a reminder to backup your files comes up and seems to take forever to go away.
4. As has been reported before, it takes a long time for cinnamon to start after you enter your password. There was some talk of using the unity-greeter rather than lighdm-greeter-gtk to speed things up. I tried this but saw no difference.

Still I do like it.

---

### Post by NormanFLinux on 2012-12-07
On Snowlinux, I replaced the default LightDM login with GDM.

I was getting a "Low Graphics" mode error with LightDM. Switching the login managers addressed that issue on my netbook.

---

### Post by wlake on 2012-12-07
> **NormanFLinux said:**
> On Snowlinux, I replaced the default LightDM login with GDM.

I was getting a "Low Graphics" mode error with LightDM. Switching the login managers addressed that issue on my netbook.

Thanks for your suggestion. Tried it, but unfortunately no effect.
Regards,
wlake

---

