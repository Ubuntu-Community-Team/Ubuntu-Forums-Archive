---
title: "Openoffice - very slow once opened"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by MaxVK on 2008-02-24
I'm running Ubuntu 7.10 and OO 2.3.0

Iv searched around the forum and found several threads about OO being slow, but they all seem to be talking about the speed of startup. I don't have that problem.

However, once OO is open if I try to create a database or spreadsheet, the program is agonizingly slow to open dialogs, or change between tables and queries for example. Loading the database/spreadsheet might be fine, but actually doing anything with it once its open is not.

I'm not talking about huge amounts of data either. If I create a new database, once I reach the point where OO is actually open on screen and I am about to create tables etc, the speed drops to almost nothing.

Are there any tweaks that I can use to speed things up, or is there an alternative to OO?

Cheers

Max

---

### Post by bwallum on 2008-02-24
Can you list the hardware specs please, you may need more memory. Failing that I would uninstall and then reinstall OpenOffice. You need to use System>Administration>Synaptic Package Manager, then search for OpenOffice. Take a note of any files removed in addition to the ones you select. Then reinstall then all. I get terriffic response from OO so its not the software per se.

---

### Post by MaxVK on 2008-02-24
Thanks for the reply. No its not the system, which is performing extremely well with everything else in Ubuntu.

XP 3000+
4G RAM
NVIDIA 6800
Creative Live
Loads of space

The word processor in OO works well, its just the spreadsheet and database that are slow, and then, its only once they have opened.

---

### Post by slimdog360 on 2008-02-24
install the proper version of java and see if that does anything. Its in the repos somewhere, look for 'sun jre'

---

### Post by sayakb on 2008-02-24
@OP
Abiword (word processor for XFCE) is much faster than OO

Also try this:

```
sudo apt-get install preload
```

This pre-caches all the mostly used apps so that it opens faster when you access it even for the first time.

---

### Post by MaxVK on 2008-02-24
slimdog360: sun-java6-jre is already installed. There is another version (5) that is not installed.

LinuxIsInnovation: Preload is fine for making a program open faster, but I don't have a problem with that. OO opens quite fast enough. Its once its open that it slows down.

Abiword. Iv not looked at it yet, but in all honesty the OO word processor seems to be fairly good anyway. It the database and spreadsheet that are driving me up the wall.

regards

Max

---

### Post by skymera on 2008-02-24
in OpenOffice settings

change the max memory to 128mb and objects to 20.

scroll down to Java and disable it.

quicken things up, a quick google search revealed these

---

### Post by kooolrock on 2008-02-24
> **LinuxIsInnovation said:**
> @OP
Abiword (word processor for XFCE) is much faster than OO

Also try this:

```
sudo apt-get install preload
```

This pre-caches all the mostly used apps so that it opens faster when you access it even for the first time.
unfortunately AbiWord is sub-standard and v.buggy, with lots of featrues lacking in it.

---

### Post by kooolrock on 2008-02-24
> **MaxVK said:**
> I'm running Ubuntu 7.10 and OO 2.3.0

Iv searched around the forum and found several threads about OO being slow, but they all seem to be talking about the speed of startup. I don't have that problem.

However, once OO is open if I try to create a database or spreadsheet, the program is agonizingly slow to open dialogs, or change between tables and queries for example. Loading the database/spreadsheet might be fine, but actually doing anything with it once its open is not.

I'm not talking about huge amounts of data either. If I create a new database, once I reach the point where OO is actually open on screen and I am about to create tables etc, the speed drops to almost nothing.

Are there any tweaks that I can use to speed things up, or is there an alternative to OO?

Cheers

Max
if ur problem is not solved, install ms office in wine.

---

### Post by sayakb on 2008-02-24
> **kooolrock said:**
> unfortunately AbiWord is sub-standard and v.buggy, with lots of featrues lacking in it.

Hmm dunno, just using oo myself..

---

### Post by bwallum on 2008-02-24
If should fly with that kit. I use spreadsheets all the time in OO and reckon it beats Excel hands down. Your cpu will get used a lot for bigger spreadsheets. The XPs can run quite hot. It may be worth checking that it is not throttled. Get your pc hot then go into the bios and check temps. Check any throttle settings based on cpu temp.

Re databse -  I have tried using the database with the default HSQL and it is dire in my humble opinion. You really need to use a decent sql engine like MySQL.

---

### Post by MaxVK on 2008-02-24
skymera: I already set the memory to 100mb and there were 20 objects set by default. I tried with and without java and the only difference was that without java I couldn't even look at database tables (Didn't check other apps)

kooolrock: I just moved from Windows and Office, so if I'm going to install office under Wine I might as well reboot the machine and re-install Windows! MS Office is not an option ;)

bwallum: Indeed, everything else seems to work perfectly well. There is no throttling going on and there are no temperature problems. I built this machine myself sometime ago and even running flat out rendering something my temperature doesn't go any higher than about 43.

---

### Post by bwallum on 2008-02-24
Did you try uninstalling and reinstalling? (has to be done through synaptic)

---

### Post by bwallum on 2008-02-24
Another thing to try and identify what is happening:-

Load a 'slow' spreadsheet then have a look at performance in System>Administration>System Monitor:'Resources' tab.

Anything going flat out?

---

### Post by MaxVK on 2008-02-24
Hmm thats a good idea: I checked the system resources and nothing maxed out. Even while OO was apparently chugging away trying to load a table of data the graphs remained fairly stable - They moved up and down as usual, but nothing topped out.

This is most strange now. OO is clearly having some trouble when it comes to creating or working with these items, but the system is simply purring along as normal, so its not about a bottleneck in the hardware (and this is the only program that has had any trouble at all since I installed Ubuntu over Windows).

I think the only thing left to do is uninstall and reinstall (Via Synaptic) and see what happens.

Thanks for all your help guys. Ill drop back when Iv reinstalled and let you know if there is any improvement.

Regards

Max

---

### Post by MaxVK on 2008-02-25
So! OpenOffice has now been removed and re-installed via Synaptic and while everything opens fast enough, the problem with the database and spreadsheet programs remains.

My hardware still shows that its not being stressed, and OO still continues to stagger as soon as I start trying to make/open/manipulate a database. The spreadsheet works fine until I open a large spreadsheet (Its only about 1500 rows so its not *that* big), and from then on performing any operation takes an insane amount of time.

Meanwhile the word processor works extremely well, even with very large files and I'm in the process of writing my own database program to handle my data. But I'm still confused by the strange problem with the database and spreadsheet programs, so if anyone has any more idea I'm open to them!

Thanks for all your help so far

Regards

Max

---

### Post by bwallum on 2008-02-25
Try running 'htop' in a terminal to see if you can pin down which processes are involved.

---

### Post by bwallum on 2008-02-25
You might also want to take a look at Tools>Options>OpenOffice.org Calc (in OpenOffice Calc). See if there are any settings that could lock up OpenOffice like Calculations:iterations, Sort Lists:format, Grid:resolution etc.

Its probably a good time to file a bug if you get no improvement after all the work you have put in.

---

### Post by crjackson on 2008-02-25
This could possibly be already fixed.  I personally do the NON-RECOMENDED thing and ENABLE every repository listed under the software sources, including proposed gutsy updates.  There were many OO updates.  I've had no problems on the 10 systems I administer at home, but this is warned against by others.

I have OO spreadsheets that have more than 3,000 lines of information and I don't have this problem at all.  Perhaps it was something fixed in one of my updates.

---

### Post by MaxVK on 2008-02-26
> You might also want to take a look at Tools>Options>OpenOffice.org Calc (in OpenOffice Calc). See if there are any settings that could lock up OpenOffice like Calculations:iterations, Sort Lists:format, Grid:resolution etc.

Iv been through the settings quite a bit now and I can see nothing that could be expected to make the program slow down like this.

> Its probably a good time to file a bug if you get no improvement after all the work you have put in.

What is there to report? It works fine for most other people, but not on my hardware. I can imagine what the developers would say, since Id say the same thing: Whatever is at fault its not OO.

Id understand such a comment, but the point is that OO has done this since I installed Ubuntu. If there is some kind of conflict then it was present before I installed anything besides the basic OS and what comes with it.

Although I cant see it somehow, perhaps there is something in my hardware configuration that OO just doesn't like?

crjackson: I can appreciate that if there is some kind of bug that I'm being unlucky enough to discover, it might have already been fixed. However, I'm still fairly new to Ubuntu and I really don't think I have the experience (Or the confidence if I'm honest) to go against basic recommendations.

Id rather work around this problem that potentially cause myself a raft of other ones that might not be quite so manageable!

---

### Post by bwallum on 2008-02-26
I'd say the OO devs would be pleased to get your report. OO isn't working for you. The most you will get involved in is sending a simple report, you can append your spreadsheet and the output from 'sudo lshw'. It will help us all out if there is a problem with OO and if the problem is with your configuration then the devs will put you right I'm sure.

[Launchpad]("https://answers.launchpad.net/ubuntu/+addquestion/+login") can be useful for this purpose. You need to open an account but it is very simple to do.

---

### Post by MaxVK on 2008-02-27
I guess you might be right there. Ill get onto launchpad as soon as I get a chance and let them know. Who knows, I might even get a solution out of it!

Thanks for all your time.

Regards

Max

---

