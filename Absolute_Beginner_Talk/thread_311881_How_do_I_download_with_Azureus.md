---
title: "How do I download with Azureus?"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by jingo811 on 2006-12-03
I want to bittorent this file
[http://torrentfreak.com/sundance-winner-the-corporation-released-for-free-on-bittorrent/](http://torrentfreak.com/sundance-winner-the-corporation-released-for-free-on-bittorrent/)
but it only starts the defult bittorent program, how do I assign Azureus to open it?  I can't find it when I browse for it.

---

### Post by johnnymac on 2006-12-03
Do this:

1.  Open azureus

2.  Click the Open icon

3.  Click the Add Files in the "Open Torrents" dialogue and add your file

4.  Click the Browse button and the location you want the file to download to.

5.  Click OK

That should do it...

---

### Post by fatbastard spice on 2006-12-03
Another way to set this up is:

* save the file to somewhere, say the Desktop
* right click on the file and choose the properties command
* in the Open With tab choose Azureus and click OK

If Azureus isn't one of the options available in the Open With tab you'll need to click on the Add button and choose Azureus from the list of programs available.

---

### Post by jingo811 on 2006-12-05
> * right click on the file and choose the properties command
* in the Open With tab choose Azureus and click OK

If Azureus isn't one of the options available in the Open With tab you'll need to click on the Add button and choose Azureus from the list of programs available.

Yes it's this part I'm having problems with I can't find it.
Could you point me to the specific path way?
Until now I've always looked in path way
/usr/bin/
when adding other programs but this time this trick didn't work.

---

### Post by nikolaos on 2006-12-05
open a terminal and give
```
which azureus
```
that should give you the absolute pathname.

---

### Post by aliyanage on 2006-12-05
also you can use this command:

```
whereis azureus
```

regards
Andrew

---

### Post by jingo811 on 2006-12-05
Weird I can't find it?  I mean I can start it up by clicking on its icon in the menu bar.  But when I search for it it's like it has never been installed.
> mike@sanka:~$ **which azureus**
mike@sanka:~$ **sudo which azureus**
mike@sanka:~$ **whereis azureus**
azureus:
mike@sanka:~$ **sudo whereis azureus**
azureus:
mike@sanka:~$


---

### Post by aliyanage on 2006-12-05
hmm... that's strange, I would double check in automatix whether it really got installed. If it is give it another try uninstalling it and installing it again. I installed my azureus over automatix as well, and I do find the path with the whereis command...

---

### Post by nikolaos on 2006-12-05
did you install azureus from a tar.gz
or did you 
```
sudo apt-get install azureus
``` 
?
if you did it from a source file, i think the icon launches from /opt/azureus/azureus

---

### Post by jingo811 on 2006-12-05
It was as I had suspected Azureus never got recognized by Ubuntu when I installed with an old version of Automatix.  The Automatix2 upgrade just reached me  this very moment.

However I uninstalled it via Automatix and instead installed via Synaptic.
Now I can find its pathway with your commands.  Tnx for the help :)

---

### Post by hotbrainz on 2006-12-05
One quick tip.....

When i do downloads with Azureus.. I normally drag and drop the download link to the downloads section and that is it. 2 "Ok"s and off it goes.

Easy dude.... :)

---

