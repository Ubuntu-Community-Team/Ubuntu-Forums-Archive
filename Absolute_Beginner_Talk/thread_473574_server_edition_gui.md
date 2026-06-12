---
title: "server edition gui ???"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by Nortonw on 2007-06-14
Hi All
This is anouther Ubuntu Server Gui install post.

I have read as many as I can find but they all relate to installing the desktop software through an internet connection.

I want to use Server edition in a server enviroment and hence no Internet access FullStop.

How do I install the Gnome or Kde Desktop with out access to the internet?

Someone asked the question before but never got an answer.

I will need a complete noddy guide as I'm rubbish with command line.

Thanks

I do have internet connection for downloading packages etc onto cd but not for the server to connect to.

---

### Post by Kobalt on 2007-06-14
What you can do is download an AlternateCD corresponding to your Ubuntu server (7,04 for example) and add it to your sources.list with ```
sudo apt-cdrom add
``` Then you can install desktop packages from this CD.

---

### Post by Nortonw on 2007-06-14
Great.

I'll try it now.
I knew it would be done by changing the source to something else.
just didnt know how.

Thanks
I'll try.

---

### Post by Kobalt on 2007-06-14
You're welcome.

---

### Post by Nortonw on 2007-06-14
OK
At the risk of sounding completely stupid.
What do I run now to get the KDE enviroment loaded?

If I do an apt-cache search all I get is a whole load of modules but I cant see what I need to run or how to start it when it is installed??

Sorry

---

### Post by seshomaru samma on 2007-06-14
to install KDE run the coomand:
```
sudo aptitude install kubuntu-desktop
```
i think it will install kdm so just run the command kdm
if this doesn't work then:
```
startx
```

---

### Post by Nortonw on 2007-06-14
Ok

I have downloaded the alternative cd for Server and have run the 
apt-cdrom add

if I now run 
apt-cache search kubuntu-desktop

I get nothing

If i run

apt-get install kubuntu-desktop

Again nothing??

What is going wrong?
Does the Server CD not have these packages on it??
Where can I get a CD with all the packages on it for this??
I'm starting to get desperate now as I dont want to use Kubuntu as the server OS for Vmware.

Thanks

---

### Post by Nikron on 2007-06-14
The server cd does not have these packages, you need to grab the regular kubuntu install cd

---

### Post by Nortonw on 2007-06-14
I have that aswell but it has made no difference??

I would have thought that it would be on the Kubuntu cd as its installed by default?
Do I need to extract the packages or something??

---

### Post by Nortonw on 2007-06-14
Surely I cant be the only person in the world to want to do this?

Has anyone got any experience of this??

---

### Post by jvc26 on 2007-06-14
I'm pretty sure you have to have the Alternate install cd version to use the cds as apt repositories. Grab yourself an alternate install cd version of kubuntu (if you want KDE) or Ubuntu (if you want gnome) or both (if you're that way inclined!) Then try again. The live cd versions to my knowledge cannot be used as apt repos.
Il

---

### Post by Nortonw on 2007-06-14
I downloaded the alternative version ealier but no joy with those commands ??

I ticked the box for alternative on the download page anyway.
How can I check the CD ??

---

### Post by jvc26 on 2007-06-14
By checking the cd - are you referring to an md5 checksum? If so check the psychocats ubuntu page in my sig, under the section of burning the cd.
Il

---

### Post by Nortonw on 2007-06-14
I meant how do I know if its the alternative version?

I have the following from what an apt-cdrom add tells me.

Disk Name = Ubuntu-Server 7.04 _Feisty Fawn_- Release i386 (20070415)
DSA Key Id FBB75451

then it says about

deb cdrom:[Ubuntu-Server 7.04 _Feisty Fawn_- Release i386 (20070415)]/ feisty main restricted

Does this help any ??

---

### Post by Nortonw on 2007-06-14
Hmmm

Just tried to install a VM with the above so called Alternative and it appears to do a normal server install with limited graphics like before.

I put a tick in the box on the download page for the Alternative version and this is what I got.

How do I know if it is the Alternative version??

---

### Post by Nortonw on 2007-06-14
OK

I have decided to download new ISOs from a different location.

Both Iso's K and U buntu  are labelled Aternative.

Hopefully we will have more joy tommorow.

Thanks
Guys

---

### Post by Nortonw on 2007-06-15
OK

Downloads completed over night but still no joy.

The packages called kubuntu-desktop or ubuntu-desktop do not exist on those cds ??

Does anyone have any ideas on this??

New day. New start

At least now I have all the available CDs.

---

### Post by hyper_ch on 2007-06-15
Well, you first have to update the available packages:

```

sudo apt-get update

```

and then

```

sudo aptitude install kubuntu-desktop

```

But why do you want to have a gui on a server anyway?

---

### Post by Nortonw on 2007-06-15
Ok

After searching through the Kubuntu Alternate Cd manually I have found .Deb file relating to kde.

I ran **Apt-cdrom add **again and then followed it up with **Apt-get install kdesktop**

I also ran **apt-get install kdm **which also installed some file but how do I now start it ??

---

### Post by Nortonw on 2007-06-15
Progress

After a reboot I get a logon screen for KDE

Once I've logged on I just get a blank screen with no task bar or icons??

Just a mouse pointer and no way to do anything else?

what can i do?

---

### Post by hyper_ch on 2007-06-15
Why don't you install the desktop version (alternate or from the desktop cd) and add the server stuff later?

---

