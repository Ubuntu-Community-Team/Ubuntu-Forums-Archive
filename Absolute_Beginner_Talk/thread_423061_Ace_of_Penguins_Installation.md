---
title: "Ace of Penguins Installation"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by RealG187 on 2007-04-25
I have [this]("http://putstuff.putfile.com/72756/1306377") file named "ace-1.2.tar" for Ace of Penguins. How do I install it? I am in [k]ubuntu 6.10...

---

### Post by taurus on 2007-04-25
Make sure you are in the directory where that file it.  Then, untar it with

```
tar xvf ace-1.2.tar
cd ace-1.2
ls -la
```
Post the output of the last command here.

---

### Post by RealG187 on 2007-04-25
The file was .tar.gz, so I took out the .gz so it would work with the commands you have.

I got this

```

total 512
drwxr-xr-x 6 mpg mke   4096 2001-05-06 21:18 .
drwxr-xr-x 3 mpg mke   4096 2007-04-25 19:09 ..
-rw-r--r-- 1 mpg mke  17340 2001-04-07 21:19 aclocal.m4
-rw-r--r-- 1 mpg mke    326 2001-04-07 21:19 AUTHORS
-rw-r--r-- 1 mpg mke   5113 2001-05-06 21:17 ChangeLog
-rwxr-xr-x 1 mpg mke  31228 2001-04-07 21:19 config.guess
-rw-r--r-- 1 mpg mke      0 2001-04-07 21:19 config.h.in
-rwxr-xr-x 1 mpg mke  24535 2001-04-07 21:19 config.sub
-rwxr-xr-x 1 mpg mke 110246 2001-05-06 21:16 configure
-rw-r--r-- 1 mpg mke   2895 2001-05-06 21:16 configure.in
-rw-r--r-- 1 mpg mke  18052 1999-02-20 13:37 COPYING
drwxr-xr-x 2 mpg mke   4096 2001-05-06 21:14 docs
drwxr-xr-x 2 mpg mke   4096 2001-05-06 21:13 games
-rw-r--r-- 1 mpg mke    442 2001-04-07 21:19 INSTALL
-rwxr-xr-x 1 mpg mke   5598 2001-04-07 21:19 install-sh
drwxr-xr-x 3 mpg mke   4096 2001-05-06 22:10 lib
-rwxr-xr-x 1 mpg mke  96494 2001-04-07 21:19 ltconfig
-rw-r--r-- 1 mpg mke 110534 2001-04-07 21:19 ltmain.sh
-rw-r--r-- 1 mpg mke    122 1999-02-20 13:37 Makefile.am
-rw-r--r-- 1 mpg mke  10482 2001-05-05 21:49 Makefile.in
-rwxr-xr-x 1 mpg mke   6283 2001-04-07 21:19 missing
-rwxr-xr-x 1 mpg mke    603 2001-04-07 21:19 mkdist
-rwxr-xr-x 1 mpg mke    722 2001-04-07 21:23 mkinstalldirs
-rw-r--r-- 1 mpg mke    142 2001-05-06 21:16 NEWS
-rw-r--r-- 1 mpg mke    238 2001-04-07 21:19 README
drwxr-xr-x 2 mpg mke   4096 2001-05-06 21:13 tests

```

Some of the text was colored, does that matter?

---

### Post by jimrz on 2007-04-25
> **RealG187 said:**
> I have [this]("http://putstuff.putfile.com/72756/1306377") file named "ace-1.2.tar" for Ace of Penguins. How do I install it? I am in [k]ubuntu 6.10...

why go to all that trouble when ace of penguins v 1.2-8 is in the repo's and may be installed using synaptic?

---

### Post by RealG187 on 2007-07-09
> **jimrz said:**
> why go to all that trouble when ace of penguins v 1.2-8 is in the repo's and may be installed using synaptic?

Could I sudo apt-get install [color=red]SOmething goes here[/color] and then just burn the deb from "/var/cache/apt/archives"

---

### Post by jimrz on 2007-07-09
> **RealG187 said:**
> Could I sudo apt-get install [color=red]SOmething goes here[/color] and then just burn the deb from "/var/cache/apt/archives"

should work
```
sudo apt-get install ace-of-penguins
```

---

### Post by RealG187 on 2007-07-16
I installed it but cannot run it, I looked under games and it doesnt appear to be there!!

---

### Post by click4851 on 2007-07-16
do a search....don't forget /usr/local, some stuff likes to go there.

---

### Post by RealG187 on 2007-07-17
HOw do I run it, usually you run things from the Menu [KDE Menu (Kubuntu) or Application Menu ([Gubuntu]("http://bestwikiever.wikidot.com/Ubuntu"))]

---

### Post by RealG187 on 2007-07-17
```

?package(ace-of-penguins):needs="X11" section="Games/Card"\
  title="Penguin Freecell" command="/usr/games/ace_freecell"
?package(ace-of-penguins):needs="X11" section="Games/Card"\
  title="Penguin Golf" command="/usr/games/ace_golf"
?package(ace-of-penguins):needs="X11" section="Games/Puzzles"\
  title="Penguin Mastermind" command="/usr/games/ace_mastermind"
?package(ace-of-penguins):needs="X11" section="Games/Puzzles"\
  title="Penguin Merlin" command="/usr/games/ace_merlin"
?package(ace-of-penguins):needs="X11" section="Games/Puzzles" hints="Mines"\
  title="Penguin Minesweeper" command="/usr/games/ace_minesweeper"
?package(ace-of-penguins):needs="X11" section="Games/Puzzles"\
  title="Penguin Pegged" command="/usr/games/ace_pegged"
?package(ace-of-penguins):needs="X11" section="Games/Card"\
  title="Penguin Solitaire" command="/usr/games/ace_solitaire"
?package(ace-of-penguins):needs="X11" section="Games/Card"\
  title="Penguin Canfield" command="/usr/games/ace_canfield"
?package(ace-of-penguins):needs="X11" section="Games/Card"\
  title="Penguin Thornq" command="/usr/games/ace_thornq"
?package(ace-of-penguins):needs="X11" section="Games/Board" hints="Mahjongg"\
  title="Penguin Taipei" command="/usr/games/ace_taipei"
?package(ace-of-penguins):needs="X11" section="Games/Board" hints="Mahjongg"\
  title="Penguin Taipei-Editor" command="/usr/games/ace_taipedit"


```I searched and got this in a text file. Ace OP is actually a set of games so maybe thats were I am going wrong, I can find "Mines" in the menu as Minesweeper is in the set, but I cant find "pegged" which was the whole reason why I got this package (seen it in DSL...)

---

