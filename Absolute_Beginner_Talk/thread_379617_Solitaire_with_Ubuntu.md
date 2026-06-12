---
title: "Solitaire with Ubuntu?"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by genosmm on 2007-03-08
A Windows friend who is thinking about trying Linux asked me if Ubuntu came with Solitaire.

I do not play card games on a PC so did a search and found Native Games [http://doc.gwos.org/index.php/Native_Games](http://doc.gwos.org/index.php/Native_Games)  Checked under Board Games but did not find Solitaire.

If Solitaire is not bundled with Ubuntu what must she do to install it?  

Thanks

Gene

---

### Post by Ek0nomik on 2007-03-08
If you run a search in Synaptic for "Solitaire" you get some results.  I found a few that you can install to play just by doing that.

---

### Post by Quillz on 2007-03-08
Yes, you can install Solitaire, and many of the avialable edition feature multiple version of the game, and not just Klondike, like on Windows.

---

### Post by xpod on 2007-03-08
Ubuntu comes with "aisleriot solataire" already installed which is a few different versions in one as far as i know.

Thats about all i`ve been able to get my wife doing with a computer this last year of having the things....bloody solataire or patience!

---

### Post by old_geekster on 2007-03-08
Ubuntu Edgy Eft 6.10 comes with two different solitaire games in the default installation.

She could use "Synaptic Package Manager" to locate other solitaire games.  Synatic has a built-in catalog of programs.  This makes it handy.  She can install any program in the catalog from Synaptic.

---

### Post by genosmm on 2007-03-09
Thanks everyone for the input.

Was thinking in the "Windows Box" when posted the question.

She will 1st be trying the  Ubuntu 6.06 LTS CD to check if the "Windows Addiction" can be overcome.

Bottom line: Since "AisleRiot" is part of Gnome-Games then she has to use Gnome?

Is there a Solitaire with KDE?  My quick search found nothing. [http://www.kde.org/](http://www.kde.org/)

Thanks again

Gene

---

### Post by Patrick K on 2007-03-09
AisleRiot will run in Kubuntu. Might have to download, I don't know. 

It has 81 solitaire games included. Should keep her happy.

---

### Post by x1a4 on 2007-03-09
Hi,

pySol is a collection of over 200 solitaire games.  It's in the repositories.

---

### Post by slushbucket on 2007-04-24
Hi All,

I have a somewhat related issue with respect to Pysol.  I was happily using the game in 6.10 and, when I did an upgrade to 7.04, the game is there, it works, but there is no sound available.  The checkbox for sound is grayed out.  I have sound-related packages installed, and I have uninstalled and re-installed everything with the same results.
The pysol home page makes reference to distributions changing sound settings - [Pysol home page]("http://www.pysol.org/").
Can anyone enlighten me as to how to get sound working?

Thanks!

---

### Post by mannequin on 2007-04-24
Did you install pysol-sound-server and pysol-sounds?

-M.

---

### Post by Sef on 2007-04-24
> Did you install pysol-sound-server and pysol-sounds?


I have the same problem.  The dependencies have changed.

From the terminal:

> Leave the following dependencies unresolved:
pysol-sound-server recommends pysol (>= 4.82-1)
pysol-sounds recommends pysol (>= 3.40-1)


---

### Post by slushbucket on 2007-04-24
Yes, I did install (then uninstall and re-install) pysol-sounds and pysol-sound-server.  Still no sound.  By the way, I did not mention before that I am running the 64-bit version of Feisty - don't know if it makes any difference or not.
Thanks for your reply.

---

### Post by robertwoes on 2007-04-27
same problem here.

from the terminal:

robertwoes@robertwoes-desktop:~$ pysol
PySol: pysolsoundserver module not found, sound disabled.

---

### Post by dreamsayer on 2007-04-29
> **slushbucket said:**
> Hi All,

I have a somewhat related issue with respect to Pysol.  I was happily using the game in 6.10 and, when I did an upgrade to 7.04, the game is there, it works, but there is no sound available.  The checkbox for sound is grayed out.  I have sound-related packages installed, and I have uninstalled and re-installed everything with the same results.
The pysol home page makes reference to distributions changing sound settings - [Pysol home page]("http://www.pysol.org/").
Can anyone enlighten me as to how to get sound working?

Thanks!
I have the same problem. The sound worked fine in Edgy. Anyone?

---

### Post by ksamvel on 2007-04-29
Was looking for Card Games set for KUbuntu 7.04 and stopped my choice on PySol. Installed everything including sound-server but do not have any Sounds. Can not solve given issue yet.

---

### Post by TFrog on 2007-05-05
I too have pysol loaded in Kubuntu 7.04 and am having the same issue as the others.  No sound and the sound checkbox greyed out.  Originally, I couldn't even load the game even from the command line.  I submitted a bug on it while using Herd 4 of Feisty and it got fixed and is now playable.  However, when I submitted a bug report about this problem there was no activity on it for 15 days and it got removed from the bug list.  Maybe I'll submit the bug again.

---

### Post by ashnazg on 2007-05-13
Same problem here, with Feisty as released on 7.04, on AMD64...

The "Sound" option on the Options menu is grayed out...

Launching pysol at command-line throws "PySol: pysolsoundserver module not found, sound disabled." error, but does still launch pysol.

And searching for help landed me on this forum thread...

So, it's 5/13/2007 on an up-to-date Feisty AMD64 installation, and this issue remains.  I can't seem to get a launchpad registration email to arrive, so I can't open a bug about it...

I hope by posting here I'll get notified of responses, and that someone will respond with a fix ;)
Chuck

---

### Post by TFrog on 2007-05-17
> **ashnazg said:**
> Same problem here, with Feisty as released on 7.04, on AMD64...

The "Sound" option on the Options menu is grayed out...

Launching pysol at command-line throws "PySol: pysolsoundserver module not found, sound disabled." error, but does still launch pysol.

And searching for help landed me on this forum thread...

So, it's 5/13/2007 on an up-to-date Feisty AMD64 installation, and this issue remains.  I can't seem to get a launchpad registration email to arrive, so I can't open a bug about it...

I hope by posting here I'll get notified of responses, and that someone will respond with a fix ;)
Chuck

ashnazg,

I just posted this issue on Launchpad for the second time.  The first time it expired.  This time I encluded the url to this very thread.  Hopefully something will get done about it.

---

### Post by roseway on 2007-06-09
There's a very simple solution to this problem (it works in Mint Cassandra, so I presume it works in Ubuntu 7.04).

```
sudo cp /usr/lib/python-2.4/site-packages/pysolsoundserver.so /usr/share/games/pysol/
```

You should now be able to change the sound setting to 'Sound enabled'. There's a bug in Pysol which makes it crash when you change the sound setting, but the change still sticks.

Eric

---

### Post by dreamsayer on 2007-06-10
Thanks for the tip I have sounds in PySol now! However in Ubuntu 7.04 you need to remove the "-" character after python.

```
sudo cp /usr/lib/python2.4/site-packages/pysolsoundserver.so /usr/share/games/pysol/
```

> **roseway said:**
> There's a very simple solution to this problem (it works in Mint Cassandra, so I presume it works in Ubuntu 7.04).

```
sudo cp /usr/lib/python-2.4/site-packages/pysolsoundserver.so /usr/share/games/pysol/
```

You should now be able to change the sound setting to 'Sound enabled'. There's a bug in Pysol which makes it crash when you change the sound setting, but the change still sticks.

Eric

---

### Post by roseway on 2007-06-11
> However in Ubuntu 7.04 you need to remove the "-" character after python.

That was a mistake by me. Thanks for correcting it.

Eric

---

### Post by sturat on 2007-06-11
you tell your friend, "screw solitair, it's all about tetravex and mahjong!!!"

:D

---

### Post by TFrog on 2007-06-15
Nice work dreamsayer and roseway.  I now have sound in pysol.  Wish someone would have found this solution earlier.  Now if we can just get someone to come up with a Debian package/packages for Alien Arena it would be great.  As to the one parties comment on tetravex and mahjong, I think he's been in a cave too long.  More people use computers to play solitaire and first person shooters than either of those games.

---

