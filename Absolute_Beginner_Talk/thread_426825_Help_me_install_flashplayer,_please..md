---
title: "Help me install flashplayer, please."
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by bwolper on 2007-04-28
I have been trying to install Flashplayer on my Ubuntu 7.04.  I have an AMD processor.  I download the file without any problem.  When I try to install by following the instructions from the Adobe site, I still get an error message.  The following is what I get from my terminal:

bwolper@blaptop:~$ '/home/bwolper/Desktop/install_flash_player_9_linux/flashplayer-installer'

ERROR: Your architecture, \'x86_64\', is not supported by the
       Adobe Flash Player installer.

bwolper@blaptop:~$ 

any help or suggestions would be appreciated.

---

### Post by bobplano on 2007-04-28
that's because you are using a 64-bit OS. try searching around for flash on amd64 or something like that. its doable but more difficult

---

### Post by apunc1 on 2007-04-28
maybe this will help

[http://ubuntuforums.org/showthread.php?t=341727&highlight=flash+64bit](http://ubuntuforums.org/showthread.php?t=341727&highlight=flash+64bit)

---

### Post by Happy_Man on 2007-04-28
Adobe doesn't want to release Flash for Linux that is compatible with x64 hardware. Why? Nobody knows. Try [http://ubuntuforums.org/showthread.php?t=388143&highlight=flash+x64](http://ubuntuforums.org/showthread.php?t=388143&highlight=flash+x64) and see if that works.

---

### Post by bwolper on 2007-04-28
Thanks for responding so promptly.  I will give it a try.

---

### Post by Sef on 2007-04-28
Check out [Gnash]("http://www.gnu.org/software/gnash/").  It 's in Add/Remove (under Applications.)  It is a GNU project, which is currently in its second alpha release.  It is fairly compatible with Flash Player 7, and will install on 64 bit systems.

---

### Post by AlexDe on 2007-04-28
Might want to check out this script that [Kilz](http://ubuntuforums.org/member.php?u=78588) wrote.

[http://ubuntuforums.org/showthread.php?t=425672](http://ubuntuforums.org/showthread.php?t=425672)

---

