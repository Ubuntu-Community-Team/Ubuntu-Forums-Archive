---
title: "bittorrent problems?"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by vinyl313 on 2008-01-09
so i have been using ubuntu dapper for a few weeks now.  It is everything i hoped for except for one problem i cant figure out.  i am having a problem with ktorrent's download speed.  i am on a 4mb connection and i my torrent downloads only get an average of 15-20kbps.  with my WD passport drive i have windows Bittorrent installed so i can boot bittorrent off that with any windows pc or laptop.   on the same connection with a windows laptop i get 100-200kbps.  so i guess my question is one of two things..  how do i fix this and get it downloading faster, or how do i install bittorrent to linux (bittorrent that is preinstalled to ubuntu isnt the right program)  [www.bittorrent.com/download]("http://www.bittorrent.com/download?csrc=header")
is the program i am trying to get, i found the linux versions yet have no clue how to install them not using synaptic

---

### Post by harold4 on 2008-01-09
What format is the external partition you are writing your downloaded torrent data to?

---

### Post by vinyl313 on 2008-01-09
i write all my data to a folder on the desktop then move it to the external once completed but the external says unknown in disk manager... so i dont know, it works fine on windows, mac, and linux.  i have never had a problem with that.

---

### Post by OffAxis on 2008-01-09
for your question #2, just download the latest .deb file from 
[http://download.bittorrent.com/dl/]("http://download.bittorrent.com/dl/")
and then navigate to the download folder and 
```
sudo dpkg -i [name of the .deb file]
```

---

### Post by harold4 on 2008-01-09
Are you dual booting and linux is slower, or is it two seperate machines?

---

### Post by vinyl313 on 2008-01-09
this might help figure out the problem....  when torrents are downloading they will say downloading and start around 1.5kbps, they will then climb in speed and get to 15-20kbps then they will drop back to 1.5 then climb again or stall then repeat the process.  i never get one solid connection

---

### Post by vinyl313 on 2008-01-09
this is a pentium 3 desktop pc with just ubuntu on it.  i tested bittorrent for windows with a dell laptop, on wireless, i am hardwired to the connection so its not my wifi connection... yet if i'm right i thought hardwired should have a better connection speed than wireless.. :-P  my eth card is 100mbps speed so it should have any problem with a stable connection thru the router

---

### Post by harold4 on 2008-01-09
There are a ton of variables, so it's tough to find a quick answer.   

For starters, make sure in your torrent client preferences, the connection properties are set properly.  There are howtos all over the net for this.

---

### Post by vinyl313 on 2008-01-09
> **OffAxis said:**
> for your question #2, just download the latest .deb file from 
[http://download.bittorrent.com/dl/]("http://download.bittorrent.com/dl/")
and then navigate to the download folder and 
```
sudo dpkg -i [name of the .deb file]
```

saved it to the desktop how do i navagate to the desktop in terminal?

---

### Post by harold4 on 2008-01-09
```

cd ~/Desktop

```

---

### Post by vinyl313 on 2008-01-09
ok package installer says it conflicts with bittorrent, and in add/remove i cannot remove bittorrent from my programs...

---

### Post by harold4 on 2008-01-09
The usual clients are:

ktorrent
deluge-torrent
and utorrent through WINE

---

### Post by aeiah on 2008-01-09
it may have something to do with port forwarding perhaps. in ktorrent you can use a UPnP plugin that'll configure your router, and for deluge you're best forwarding things on your router's control panel and testing the ports from within deluge to see if they're connected properly. i dont know about other bittorrent programs, but these two are two of the most common and are pretty good. i prefer deluge but only really because it looks nicer in gnome

---

### Post by OffAxis on 2008-01-09
conflicts with bittorrent, eh?
Have you tried removing it from the command line?
```
sudo aptitude remove [name of package]
```


```
sudo aptitude search torrent
```

will list all the packages on your system (and available in the repos) with 'torrent' in them (just in case it's literally not the 'bittorrent' package that's conflicting)

with aptitude's search option it'll return a list where: 
a = available
i = installed
v = virtual
p = no part of package on system
c = config file of package on system (leftover from a previous install)

---

