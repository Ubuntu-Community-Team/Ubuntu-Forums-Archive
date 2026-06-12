---
title: "A couple things"
date: 2006-09-22
forum: Absolute Beginner Talk
---

### Post by tsjustice on 2006-09-22
Well i just installed ubuntu the other day with basically no problems.  The only things im having problems with right now are getting mp3s to play in armorok and getting sun java on the computer.  Everytime i type in to install it from the terminal its say it cant find the package. If anyone could help me with these things it would be much appreciated.

---

### Post by skierkegaard on 2006-09-22
For the mp3 problem look at the ubuntu wiki on restricted formats.

For java, try using synaptic to look at the exact name of the package you are trying to install.

---

### Post by andypaxo on 2006-09-22
If installing from the terminal fails to find the package, you may need to enable other repositories to find what you are after. Check the following link out.
[http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories)
(That website by the way, is invaluble)

---

### Post by bulldog on 2006-09-22
Take a look at Automatix,

[http://ubuntuforums.org/showthread.php?t=80295](http://ubuntuforums.org/showthread.php?t=80295)

It can help you installing a lot of essential programs.

Take a look at it,you won't be sorry.:D

---

### Post by Metacarpal on 2006-09-22
Hi, and welcome to Ubuntu!

Have you enabled extra repositories yet?
Some packages (such as Sun Java and mp3 playback codecs) aren't in the main Ubuntu software repositories, so you have to enable additional software sources to get them.

[Here's a quick guide to doing so]("http://www.psychocats.net/ubuntu/sources").  When she says to enter in terminal, you can get to that through your Applications menu > Accessories > Terminal.

Once you get those set up, you'll be able to download the packages you need.  Here's a quick line of code you can enter in terminal to download what you need to enable playback of various multimedia codecs.  Just copy this and paste (insert+i) into terminal all at once:

```
sudo aptitude install totem-xine gxine libxine-main1 libxine-extracodecs w32codecs
```

I can't remember the names of the sun-java packages right off hand, but if you know those, you can add them on the same line after "w32codecs".  You'll be prompted to accept the license agreement.

If you wish to playback encrypted DVDs, you'll also need to install the packages libdvdread3 and libdvdcss2

For Flash, don't try to download that from the repos right now - I know there was a problem with the package the other day, and I don't know if that one's been fixed.  Instead, follow the instructions [here]("http://www.ubuntuforums.org/showthread.php?t=262180").

---

### Post by tsjustice on 2006-09-22
Thanks for all the quick replies. Im working on some of these suggestions and they are all great. Thanks

Edit: thanks got everything i wanted working, but i was just wondering how to launch the 3d desktop from the terminal?

---

