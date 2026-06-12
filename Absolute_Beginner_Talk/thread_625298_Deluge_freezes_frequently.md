---
title: "Deluge freezes frequently"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by ryanVickers on 2007-11-27
Does anyone else use this program?  I think it's really good, but it tends to freeze all the time! :mad: That actually wouldn't be so bad, but on top of that, things tend to randomly lose several completed percent when this happens (***!!).  Any ideas on why or how to fix this?

---

### Post by Six_Digits on 2007-11-27
Having the same problem... Simply stops anything torrent related. I can still click menus and such...

---

### Post by Cable on 2007-11-27
What version are you using?  There have been several updates to Deluge since 7.10 came out.  If you haven't already, I would suggest that you update Deluge to the latest version.  You can find a package for both 7.04 and 7.10 on their [web site]("http://www.deluge-torrent.org/News:Portal").  Or, [here]("http://download.deluge-torrent.org/index.php?dir=ubuntu/gutsy/0.5.7/&file=deluge-torrent_0.5.7-1_i386.deb") is a direct link to the file.  Try updating and trying it.  Post back here and let us know how it goes.  :-)

---

### Post by ryanVickers on 2007-11-27
I have 7.10 but just installed it a couple of days ago at most :p

It's odd - sometimes it will just go forever, but other times it will crahs within an hour!  But like I said, that's not so bad, it's the fact it loses a bunch of the data when it crashes!!! (*****!!) :p

---

### Post by Cable on 2007-11-27
I guess I should have been more specific when I was asking about versions.  I meant to ask what version of Deluge you are running, as it may be a bit of an older version.  If it's anything earlier than 0.5.7, click the link in my previous post and download the .deb file and install it.  See how that works for you.

---

### Post by ryanVickers on 2007-11-27
yeah, mines 5.4.1 or something... :p

I'll see if it does anything... Oh, and I'll get the 64 bit version ;)

---

### Post by ryanVickers on 2007-11-27
I don't know if they've fixed anything yet, but the features are sure nice! :p

---

### Post by Six_Digits on 2007-11-27
I'm running 5.7-1...

---

### Post by rahimveron on 2007-11-28
Ya a couple if times i too lost some of my completed downloads, the data just got corrupted. I loved Deluge but i went back to Azureus, at least it never corrupted the data.
I am not saying, dont use Deluge, i just shared my experience with it. When it works its all hunky-dory, but when it conks up it just ........

---

### Post by ryanVickers on 2007-11-28
I haven't had any corruption yet, but it tends to lose some of the data when it crashes somehow!! :confused::mad:

---

### Post by Six_Digits on 2007-11-28
Now it won't even start... Tried a reinstall too :-k

---

### Post by Cable on 2007-11-28
Try going into your home directory, and go into the .config folder.  Then delete the Deluge folder.  That will reset all of your options in Deluge, and it should then start again.  You'll just have to reconfigure it.

---

### Post by Six_Digits on 2007-11-28
Thanks Cable. Would this also apply to the other items in this folder?

---

### Post by Cable on 2007-11-28
It seems like most times, yes, deleting the configuration folder for an application will solve issues with that particular application acting up (unless it has genuine bugs that need fixing).  However, it won't always work.  Also, only some apps keep their config files in that .config folder.  Many other apps will simply have a .folder in your home directory.

---

### Post by Six_Digits on 2007-11-28
Ok, cool. Thanks for the info nugget.

---

