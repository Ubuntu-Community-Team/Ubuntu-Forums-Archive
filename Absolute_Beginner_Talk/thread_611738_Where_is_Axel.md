---
title: "Where is Axel"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by Da King on 2007-11-13
I was trying to get prozilla bt soo many prob with it as i read it from this forum..most of the alternate answer was AXEL. well i went to terminal and sudo install axel
after installation i continued the "man axel" and some sort of "readme" notes appears in the terminal..well now am looking for axel and i cant find it in my panels..where does some of the programs installed via the terminal go at all...why does doesnt it have shortcuts on the desktop?? i try typing "axel" in the terminal and i get```
 king@King:~$ axel
Usage: axel [options] url1 [url2] [url...]

--max-speed=x           -s x    Specify maximum speed (bytes per second)
--num-connections=x     -n x    Specify maximum number of connections
--output=f              -o f    Specify local output file
--search[=x]            -S [x]  Search for mirrors and download from x servers
--no-proxy              -N      Just don't use any proxy server
--quiet                 -q      Leave stdout alone
--verbose               -v      More status information
--alternate             -a      Alternate progress indicator
--help                  -h      This information
--version               -V      Version information

Report bugs to lintux@lintux.cx
king@King:~$ 
```
 how do i use it with firefox.

---

### Post by Da King on 2007-11-15
is anyone gonna answer ma post? 

:KS

---

### Post by mali2297 on 2007-11-15
The program you installed is a command line tool. For example, if you want to download [Epoq-Lepidoptera.ogg]("http://www.vorbis.com/music/Epoq-Lepidoptera.ogg") from vorbis' web site:
```

axel http://www.vorbis.com/music/Epoq-Lepidoptera.ogg

```

There is a KDE front-end in the repositories called **axel-kapt** that you can try if you want a GUI.

If you want to use axel with firefox, see this link:
[http://poundbang.in/2006/10/21/using-axel-with-flashgot-in-firefox-on-linux/](http://poundbang.in/2006/10/21/using-axel-with-flashgot-in-firefox-on-linux/)

---

