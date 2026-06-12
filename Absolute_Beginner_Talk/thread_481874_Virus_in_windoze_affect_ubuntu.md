---
title: "Virus in windoze affect ubuntu?"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by maddot on 2007-06-23
I was wondering, if a virus in a windows partition will affect a linux os system. I have a virus on my xp partition which instead of just formating the darn thing, i need to get some files out of there....My important documents... how do i extract it without causing any harm to my ubuntu and linux partitions?

---

### Post by Alterax on 2007-06-23
You should be fine.  The vast majority of viruses depend on the kernel they are being run on and the services available to it.  Viruses that affect Windows are most often written to exploit Windows code.

Now if you aren't fully convinced, install the ClamAV antivirus from the Ubuntu repositories, mount the windows partition as Read/Write, and use Clam to scan the Win partition.

--Alterax

---

### Post by ryanVickers on 2007-06-23
Yeah, they should be fine, but it's probably good to clean them anyways if you ever move them into a windows partition again!  Most viruses, yes, would be using windows commands, and looking for windows directories to mess up.  So unless your going to keep all your files is a folder called C:/WINDOWS/system32 and  have some backwards slashes plugin, you should be fine! :p

---

### Post by vexorian on 2007-06-23
you shouldn't worry.

The age of praCtiCal Cross platform viruses is still far, far away.

Although, some of the files might be infeCted.

Know your enemy, if the files are doCs make sure the virus doesn't Copy itself to the doCuments (although it won't harm ubuntu it is not good to keep them infeCted anyways)

As a matter of faCt you Can even use ubuntu to Clean the virus, just researCh about the virus.

---

### Post by ryanVickers on 2007-06-23
do you have a virus that makes all your "c"'s capital? :p

---

### Post by SimonPhoto on 2007-06-23
Windows viruses do not bother Linux.  IMO, the only reason to have a virus scanner in Ubutu is to scan docs you got from an untrusted source, before sending them to your few remaining friends with a Windows box.

One exception:  I believe it is possible for Firefox exploits to go cross-platform - but again, if they are set to modify anythign in the system, chances are they are looking for a directory that starts with "C:\"

---

### Post by vexorian on 2007-06-23
> **ryanVickers said:**
> do you have a virus that makes all your "c"'s capital? :p
It was just after I installed compiz-fusion that I played a lot with the effects and hotkeys options, somehow I broke the "c" key, the good thing was that a reboot fixed the issue.

---

### Post by mikewhatever on 2007-06-23
You can pull out the files using an Ubuntu live cd and some external storage, or from Ubuntu installed on the hdd. Windows viruses should not affect it.

---

### Post by jcronkhite on 2007-06-23
Maybe someone else can second this, but I think a virus could affect your WINE installation (if you are using WINE of course).  Because there is a Windows directory and many viruses install there or attack known Windows directory files, they are still vulnerable.  Perhaps if you launched Word using WINE and a given document had a macro virus your WINE install could get the infection.  Would be interesting to test.  Worst thing that could happen IMO is you'd have to remove/re-install WINE I think.  Anyway, my 2 cents.  I read about this a while ago.  I know it's not the same as an infected Windows partition, but I thought this might fit here as well.

---

### Post by Tyke91 on 2007-06-23
I think a guy tried this.

out of 5 of the most common viruses, only 2 ran. one failed to affect his system, and the other failed to propogate and spread to others (it had a mild effect of taking up 20% cpu usage).

in other words, it's DAMN HARD to run viruses (or any other microsoft product) on wine or linux in general, unless the people in charge have SPECIFICALLY formated themselves to run the virus


(looking for a source now, can't remember where i saw this)

---

### Post by Tyke91 on 2007-06-23
[http://os.newsforge.com/article.pl?sid=05/01/25/1430222&from=rss](http://os.newsforge.com/article.pl?sid=05/01/25/1430222&from=rss)

got it :D 

apparently, it was a minor effect... the thing slowed his machine incredibly, but he fixed it by just closing wine :D. 

none were able to spread

---

### Post by Tyke91 on 2007-06-23
meh... sorry for the triple post.

Apparently - you can run SOME viruses under wine, but the social engineering bit (the part of a virus that tricks a user into running it) is not there.

first you would have to isolate a virus that WORKS

open and run wine

Make sure you have something that auto sends emails running through wine (outlook or something)

run the virus.



i'm pretty sure nobody is stupid enough to do that no purpose :D so i think we're safe for now

---

### Post by jcronkhite on 2007-06-23
Cool, I'm looking forward to reading about this.  Hope you find the source.  Thanks!

---

