---
title: "questions about which version to use with finickey laptop ATI hardware"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by leogibson on 2007-02-24
ive tried many releases since breezy and i cut my teeth on linux back then.  i find that dapper, edgy, and surprisingly least of all feisty herds to be very unstable, especially when it comes to ACPI (HP laptop, closed bios).  i want to be able to control my GPU temps without having to build too many obscure apps with libraries no one can find. 

i know with ATI and Nvidia not having open (or open enough drivers), this will just take time, if linux ever becomes a reliable productive desktop where enough people will want to use it and program better drivers.  the posts about cpu scaling and anything having to do with 3d acceleration tells me i should just wait till i have an older desktop laying around with a slow generic video card, but i have dreams of vista like environments with new-ish hardware even on laptops....am i crazy?

anyway, should i start with dapper and just upgrade to 2.6.20 and see what im able to do?

i want full hardware control with drivers for linux with REAL options...oh and before anyone says "well, go out and program them yourself!!!!111"  i know, im just not that leet.

the ati open source project is a start, and i know we wont be able to do much unless ati..er amd lets them open up, but cant i at least have a ati driver where i have a simple interface to control scaling, powerplay, profiles, and whatnot?

im not shure if this post belongs somewhere else or not....sorry in advance

leo

---

### Post by FyreBrand on 2007-02-24
I'm not sure what you're really asking there.  Are you looking for a version that's going to install and work on you notebook?  I would say Edgy.

I just put Xubuntu 6.10 on a PIII laptop with 120MB of memory and a 12GB hd.  It's a little slow, but it works fine.  It even fires up Open Office writer okay.  It could be a lot quicker with a lighter Desktop Environment like Fluxbox or Openbox, but it's a staff machine and it needs to be non-geek friendly.

Just a note on a couple things:
1. You're not going to get 2.6.20 kernel on Ubuntu outside of Feisty without compiling it yourself.

2. You're also not going to get massive hardware control especially on really closed hardware.  The best you're likely to get is functionality (maybe).  I'm not sure what you mean by total hardware control.  Once it's configured to do what it needs to do then what do you need to control?  If something isn't working post specifics so that we can search for an answer or someone can pipe in with ideas.

3. If you're having heating problems with the video card maybe have the laptop cleaned (fan and vent areas).  Unless you're overclocking or rendering massive 3D the gpu shouldn't have a heating problem.

4. Post your laptop model and we can try and search for an ACPI work around for that.  Some models work good and others, well they don't.

---

### Post by deadgobby on 2007-02-24
[https://wiki.ubuntu.com/?action=fullsearch&context=180&value=HP&titlesearch=Titles](https://wiki.ubuntu.com/?action=fullsearch&context=180&value=HP&titlesearch=Titles)
[https://wiki.ubuntu.com/?action=fullsearch&context=180&value=ACPI&titlesearch=Titles](https://wiki.ubuntu.com/?action=fullsearch&context=180&value=ACPI&titlesearch=Titles)
 I would like to help more, but you did not give the HP model type.

---

### Post by leogibson on 2007-02-24
sorry, this was more of a rant, but ive taken apart my laptop dozens of times (compaq v4000t) and the heat transfer pipe was so poorly designed, the gpu doent even come close to touching the copper channel.  i find i have this problem of my gpu overheating my whole laptop (next in line is the cpu of course before it reaches the system fan) but at least with the Omega drivers, i can control powerplay to lower the clock speed of the gpu, but i still havent been able to find anyway to manually find a tool to do this in linux.  ive tried the ati linux drivers and the open source ones (im still confused aty to which are which, i know theres 2, one from the community (fglrx?) and one from ATI (binary?))  anyway i know with windows its as easy as googling for a single software ati tool or ati clock tool, but ive searched and searched for a linux version or similar of this and have come up empty.

Some versions of ubuntu (dapper i think as opposed to edgy) i noticed my laptop heating quite a bit less.  but when i tried edgy my temps were nearly 70C idle as opposed to 60-65 idle with dapper (and windows without enabling gpu clock control in Notebook Hardware Control)

With nhc in windows i can keep my gpu clocked down and get temps as low as 48C, and my fan never runs.  im looking for a linux equivalent to NHC.

/rant  my bad

leo

---

