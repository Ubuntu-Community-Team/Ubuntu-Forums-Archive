---
title: "how to P2P...im stuck"
date: 2006-04-08
forum: Absolute Beginner Talk
---

### Post by x5452 on 2006-04-08
I found a link to this site   [http://dev.gentoo.org/%7Esekretarz/distfiles/](http://dev.gentoo.org/%7Esekretarz/distfiles/)
I was told it was a limewire version made for linux already.   I downloaded the file libgadu-20050719.tar.gz  (it was the latest) first is that the right file for installing limewire?  second, now what do I do with the tar.gz file to install limewire?  I read I need to install java first, but cant I just go through synaptic, select the couple java's there and install them?  then what to do about getting limewire going?  

I tried useing gnutella, but it wont do anything, not even search.

pleae advice, thanks in advance!

---

### Post by slipk487 on 2006-04-08
get [automatix]("http://www.ubuntuforums.org/showthread.php?t=138405")
it has Frostwire which is better then Limewire Free and u can use automatix to install java

---

### Post by LoclynGrey on 2006-04-08
I use firestarter firewall and Frostwire p2p (aka limewire) which I installed via automatix.
Automatix installed everything i needed.
In firestarter I just opened the relevant ports and everything works well.

---

### Post by slipk487 on 2006-04-08
ya automatix it one of the best things to use for ubuntu

---

### Post by wolfee on 2006-04-08
[QUOTE=slipk487]ya automatix it one of the best things to use for ubuntu[/QUOTE]
Ya but watch your cpu % Mine tends to max out allot with frostwire. I heard there is a bug in the code ( accidentally wrote a dos line in java I think)
Automatix is not to blame. It is the best idea for Ubuntu!!! i wish there where more like it, ones for easy driver installs maybe:-k

---

### Post by x5452 on 2006-04-08
alright, I have automatix installed, I used it to get firefox, but im not sure if i told it to get frostwire initially becausei didnt now what it was. Is there a way i can check?  \
how do you know what ports to open in firestarter? and where to set them or whatever?
finally, with gnutella, there was an icon in upper right saying i appeared to be firewalled, both tcp-wise and udp-wise.  what are these? i never installed any firewalls and i saw this before i figured out how to enable firestarter?  are there ohter firewalls pre installed and how to turn them off and use only firestarter?

---

### Post by slipk487 on 2006-04-08
frostwire should show up  in applications>internet u can check it at the automatix log were u installed automatix and it will tell u what was installeb an i dount us firestarter or a firewall i just use the on in my router so sry i cant help u with that

---

### Post by x5452 on 2006-04-09
Ok I have frostwire installed through automatix, while installing it said installing java also, I checked in synaptic and sun Java is installed. I have frostwire icon, i can click it and it opens up the frostwire screen, but then as soon as i click anything in it it freezes. I can minimize the screen, then brign it back and it is all blank white.  help

Also, is it bad that everything in my ctrl-alt-del process list is "sleeping"???  I know java is installed, it is first on the list, under status though it is sleeping, as is frostwire, which i cant even close now.  issleeping normal?

---

### Post by nalmeth on 2006-04-09
I personally use apollon, with a fasttrack (kazaa) plugin personally setup. Apollon comes with the gnutella network by default though.
Its in the repos.

---

### Post by Bloch on 2006-04-09
I have a celeron 2.4GHz with 512 MB of ram, and frostwire can go blank for 6 - 10 seconds. But otherwise it works perfectly. If your specs are significantly lower than mine then I reckon frostwire will be a pain.

Don't worry about all the processes sleeping. That's perfectly normal. Oh, and another thing about frostwire. Make sure you quit using the menu button, and not simply clicking the top right x on the window.  Otherwise java will keep running in the background for several more minutes and will slow your system to a crawl - again this depends on your specs. You might not even notice if you have a 3.2 GHz pentium. Check the list of processes to see if the java environment of frostwire "lives on" after you end it.

---

### Post by x5452 on 2006-04-09
I now used synaptic to completly remove frostwire, i then reinstalled it through synaptic. Before opening it up i went to terminal and ran 

sudo apt-get install sysutils
sudo dos2unix /usr/lib/frostwire/runFrost.sh

I then exit terminal, go to frostwire icon in menu and click.  THe frostwire box opens up fine, but whatever i click on does nothing at all.  cant close, cant click file, the 5 red signal bars in bottom left dont change.  it is just open but useless.  any ideas at all please?  I need to get p2p on this machine

---

### Post by nalmeth on 2006-04-09
> I personally use apollon, with a fasttrack (kazaa) plugin personally setup. Apollon comes with the gnutella network by default though.
Its in the repos.
sudo apt-get install apollon
apollon

when it asks you where your gIFT plugins are, they are in /usr/share/gift

disclaimer: 
A lot of times with p2p you get results you didn't search for, and see some very vulgar stuff. There is no built in filter for apollon, you have to filter your results by hand in the dialogue. This app should be rated 18A.
This app is meant for KDE, but it has worked fine for me in gnome.
I have lately noticed that some random downloads have been started, usually just songs. I know they are random because it downloads music I would never consider exposing to my ears. This is worrisome, but beyond this, apollon has got to be my fav p2p app. Perhaps when I get kmldonkey going it will get a run for its money.

If you want to stay safe take the time and get frostwire or whatever going, but this should work right away.

---

### Post by x5452 on 2006-04-09
thanks for the suggestion, any ideas on how to begin with frostwire to get it working? im not sure where to even start?

---

### Post by x5452 on 2006-04-09
ok now it is the exact same thing with limewire. I went to their site, downloaded the for linux rpm version to my desktop. i then went to terminal and installed alien, then used it to create the deb file and installed limewire. it siad everything was done fine, i exit terminal, go to limewire icon and it opens up then freezes!! no buttons work or anything.  i go to processes again, limewiere is there 'sleeping', (what does the sleeping mean, and why is everything sleeping?) i end process on limewire nothing happens, java is on top of list still, also sleeping, i end process on that and the limewire screen disappears finally. what is going on, any ideas on why this is happening please??!!?](*,)

---

### Post by nalmeth on 2006-04-09
If there is a .deb available you should always take it over an rpm. But either way, it looks like your java is really screwed up or something. Did you go through a lisence agreement in automatix when you installed java? Which version of Java did you install?
Blackdown 1.4, 1.5 JRE, or 1.5 SDK.
The best to go with is the 1.5 JRE, 1.5 SDK is supposed to be more than the average person needs.
Try the java install exclusively again in automatix. If you installed 1.5 JRE and agreed to the lisence agreement (required to install it) then I couldn't say what might be wrong.
I tried both frostwire and limewire, but I did not particularily like either of them.
If you get really fed up go with apollon - no java I don't think.
Forgot to add this:
sudo apt-get install gift apollon
Search synaptic and you might find a fasttrack plugin for the kazaa network. Gnutella and OpenFT are included.
EDIT:
Just did a quick apt-cache search fasttrack and found it in the repos.
sudo apt-get install libfasttrack-gift
Just remember to tell apollon to look in /usr/share/gift and you're all set

---

### Post by x5452 on 2006-04-09
thanks for the info. I got limewire running fine now, i had java 1.5 installed, i had to install jre1.4 and set it to default for it to work...wierd, but it works.

someone asked me earlier to do something like 'run script in terminal and report back any errors'  how do you do that, for future reference? is there a command to check an installed app?

---

### Post by nalmeth on 2006-04-09
if you know the name of the app, or at least part of the name, you can type it in the terminal and hit tab halfway through. By hitting tab, the terminal will try to complete the command for you.
Automatix can install a 'debian menu' for you, which should show all your installed apps. It sticks it in the applications menu, and is a little untidy but should show everything.
When i really need to find an app, xfce4-appfinder for the xfce desktop is excellent.
As far as the script goes, if you didn't get any directions with it, then it's hard to say what you're supposed to do with it. 
Good to see you finally got your p2p.

---

### Post by x5452 on 2006-04-10
thanks, getting that going is one less headache!  
is there a command you can type that will check a program you have installed and print a list of it?  like different files, if its ok, things like that?  do I make any sense? lol

---

