---
title: "Firefox loads other page instead of home"
date: 2006-10-22
forum: Absolute Beginner Talk
---

### Post by morpher on 2006-10-22
Hi guys, this may sound stupid, but my firefox loads another page at startup,instead of my home page...

i have my hp set to google and it opens google in a milisec (as far as i can see, just enough time for me to get the google cookie, and not enough time for me to actually SEE google), but then replaces google with arizona.edu (same window, same tab..).

i tried to solve it by reseting the homepage, and clearing all private data and cache n stuff, but it didnt solve it, everytime i open a new firefox window, i get arizona.edu..... annoying!!!

oh, and btw, if i click the homepage or alt+home, i get google, and it doesnt get replaced by arizona.edu, that only happens at 'startup'.

i'd really apreciate any kind of help, ill try whatever to get rid of this annoying thingy.

Thanks ALOT in advance :)

---

### Post by d3v1ant_0n3 on 2006-10-22
What happens if you run the command 'firefox' (without the ') in the terminal? I've seen this before, but I'm not entirely sure why it was doing it...

*edit* I just tried putting 'u%' into the url bar in firefox, and it took me to arizona.edu ...have a look at the launcher for firefox, and see if the launcher command is 'firefox u%'....I *think* that command is designed to load firefox with settings for individual users, but for some reason, also starts firefox at arizona.edu's webpage.

Hmm, indeed, just checked this...the command 'firefox <something>' opens firefox at the result you would get for typing <something> into the url bar. Odd. But handy.

---

### Post by morpher on 2006-10-22
oh cool, that was it ^^ thanks alot mate

i didnt even consider that as it was the default value in the launchers, but seems it was it's fault lol, evil launchers :evil: 

again, thanks ;)

---

