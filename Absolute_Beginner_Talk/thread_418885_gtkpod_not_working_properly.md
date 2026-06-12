---
title: "gtkpod not working properly"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by zhinker on 2007-04-22
Hi, I'm new to Ubuntu (I'm using 6.10). I tried installing gtkpod to work with my iPod mini and it seemed to go fine, but when I tried reading the music from my iPod I'd get the following error:
[INDENT]Could not open "iTunesDB.ext" for reading extended info.
Extended info will not be used.[/INDENT]
When I clicked 'okay' it would still show all the songs in my iPod but when I tried to play them I'd get this second error:[INDENT]
Could not find command 'xmms' specified for 'Play Now'[/INDENT]
I also got an error when I tried to update my iPod, it would go through the motions of updating all the songs and then I'd get the following window titled 'Failed Track Update' listing all of my songs with the text "(no filename available)" listed after each one's name like so:
[INDENT]See You (no filename available)
09-Enough Space (no filename available)
10-February Stars (no filename available)
11-Everlong (no filename available)
Walking After You (no filename available)[/INDENT]
Any ideas guys?

---

### Post by jiminycricket on 2007-04-22
Hmm...have you tried alternatives like [Floola ]("http://www.floola.com/")or Amarok?  Do they have the same problems?

Was your ipod formatted from a Mac or Windows itunes first?

---

### Post by zhinker on 2007-04-22
> **jiminycricket said:**
> Hmm...have you tried alternatives like [Floola ]("http://www.floola.com/")or Amarok?  Do they have the same problems?

Was your ipod formatted from a Mac or Windows itunes first?

It was formatted for windows.  And no, I haven't tried any other programs (looks like Amarok is a Kubuntu program so I can't use that anyways) but I'll do that now...btw, just in case it helps, Rythmbox can read and play the music easily, but of course, it can't update my iPod mini

---

### Post by zhinker on 2007-04-22
I'm not sure if I should try Floola, becuase I can only find the latest beta version and whenever I open it I get this warning telling me that the program's not stable yet and could potentially mess up my computer.  

I figured out the problem with it not playing the songs though.  It apparently calls another music player to actually play the song, and it's defaul player, xmma, was not installed.  A quick trip to add/remove and that was taken care of. 

The other problems are still there though

---

