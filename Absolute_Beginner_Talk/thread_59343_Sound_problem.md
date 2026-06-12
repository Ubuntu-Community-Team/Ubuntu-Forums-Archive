---
title: "Sound problem"
date: 2005-08-23
forum: Absolute Beginner Talk
---

### Post by sophtpaw on 2005-08-23
Hello once again,

I am begging now, for someone to help me on this ongoing and frustrating issue i have with sound. My original post of K3B had 200 viewing but only 1 person was willing to help out. That person now seems to have disappeared.

I'm trying to follow the wiki: [https://wiki.ubuntu.com/SoundProblemsHoary](https://wiki.ubuntu.com/SoundProblemsHoary) but not much joy yet.

For a start how can i change the script in esd.conf which appears to be a Read only file to what is been given in the wiki 

[esd] 
auto_spawn=0
spawn_wait_ms=100
default_options= -terminate -nobeeps -as 2

After that it is recommended to go to System/Preferences/Multimedia System Selector and change the default sink and source and change it to Alsa. 

One thing i would say is that right now it is set to esd - enlightenment sound daemon and on test works in Default Sink but does not work in Default source. I wonder what other people have theirs set at and any knowledge in untangling my sound problems, i.e:

Ubuntu uses a program called esd to allow multiple applications to access the sound card at one time. However, many third party applications not in Ubuntu main aren't designed to use esd to access the card. On some sound cards, this causes these applications to not produce sound. To work around this problem, esd must be configured to release the sound card when it is not using it. Place the following in your /etc/esound/esd.conf


would be very very appreciated,

--
sophptaw

---

### Post by glug101 on 2005-08-23
> For a start how can i change the script in esd.conf which appears to be a Read only file to what is been given in the wiki 

sudo gedit /etc/esound/esd.conf

The computer will ask for your login passwd and then allow you to edit the file with admin rights.

You also might want to take a look at the following howto for some instructions that I found very useful:

[http://ubuntuforums.org/showthread.php?t=32063](http://ubuntuforums.org/showthread.php?t=32063)

---

### Post by sophtpaw on 2005-08-24
[QUOTE=glug101]sudo gedit /etc/esound/esd.conf

The computer will ask for your login passwd and then allow you to edit the file with admin rights.

You also might want to take a look at the following howto for some instructions that I found very useful:

[http://ubuntuforums.org/showthread.php?t=32063](http://ubuntuforums.org/showthread.php?t=32063)[/QUOTE]

Thx Glug,

it is much appreciated. I must admit i had given up on any help so i switched to kde as default where i have no sound issues. It seems the problem is in Gnome only. As a noob i don't know how one is expected to be able to do all this on one's own. And after repeatedly asking for help none of the pros 'round here seemed willing, so thx 
but i'm disappointed with the experience of support here and this goes out to others reading this.  As someone who has raved about the Ubuntu forums and community i feel i'm entitled to say so, but the support to this question has been poor to be frank

Maybe they'll make an Ubuntu where those sound issues are resolved out of the box, and beginners like me do not have to search the wikis and beg for help on the forums. Don't get me wrong i'm happy to follow ubuntuguide.org follow some instructions and learn some command line along the way, and while i appreciate that Linux has come a long way from even 3,4 years ago, this certainly wasn't fun.

cordially,

--
sophtpaw

---

### Post by sophtpaw on 2005-08-24
[QUOTE=glug101]sudo gedit /etc/esound/esd.conf

The computer will ask for your login passwd and then allow you to edit the file with admin rights.

You also might want to take a look at the following howto for some instructions that I found very useful:

[http://ubuntuforums.org/showthread.php?t=32063](http://ubuntuforums.org/showthread.php?t=32063)[/QUOTE]

I followed the links instructions. but ran into failure:
transcript:
Failed to construct test pipeline for 'ALSA - Advanced Linux Sound Architecture'

which means i'm back to esd working when testing Default Sink Output but not working when Default Source Input.

sigh...

--
sophtpaw

---

### Post by glug101 on 2005-08-25
> but i'm disappointed with the experience of support here and this goes out to others reading this. As someone who has raved about the Ubuntu forums and community i feel i'm entitled to say so, but the support to this question has been poor to be frank

Yes, I've also noticed that there are a lot of unanswered posts on ubuntu forums. (hence the signature)  However, Ubuntu is by it's nature quite heavy on the newbie side. (hey, how else are we to get folks to accept it;) )  I just recently moved here from the Gentoo forums where they are quite top heavy with developers.  On Gentoo forums, I'm not needed, here I can make a difference;)  Basically, I think there will always be unanswered posts here.  I'm just trying my personal best to minimize them.

**stepping down from high horse**

Sound problems, $^#&! there seems to be a lot of these here!  I'm hoping the next release has some better functioning sound.  I remember that I had errors on the test for my sound also, but upon restart of the computer my sound worked perfect.  Your mileage may vary though.

---

### Post by WirelessMike on 2005-08-25
[QUOTE=sophtpaw]One thing i would say is that right now it is set to esd - enlightenment sound daemon and on test works in Default Sink but does not work in Default source. I wonder what other people have theirs set at and any knowledge in untangling my sound problems... [/QUOTE]
My settings are:
Default Sink: ESD
Default Source: OSS

Been working fine for a long time here.

---

### Post by sophtpaw on 2005-08-25
[QUOTE=WirelessMike]My settings are:
Default Sink: ESD
Default Source: OSS

Been working fine for a long time here.[/QUOTE]


It goes without saying that i have tried all the combinations. I am glad to hear that all is working and well with your os. When you have some idea how to help me work mine that'll be great too,

regards,

sophtpaw

---

