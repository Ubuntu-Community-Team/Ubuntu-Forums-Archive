---
title: "[SOLVED] Need custom command for .torrent files."
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by whoscheesemine on 2008-03-07
I'd like to use a custom command to set all .torrent files to automatically open with Utorrent through WINE. What is the command I should use?

---

### Post by uberlube on 2008-03-07
Uhm, Im not sure if that is even possible. If it is it would have to be done from within Utorrents settings. Also why are you using a torrent program through wine when there are so many good open source ones that run perfectly in linux?

---

### Post by Nythain on 2008-03-07
A. it is possible, i used to do it... its not so much a custom command as it is telling firefox to associate/run a specific script (and i dont remember the contents of said script) upon clicking on a torrent file in firefox...

B. its been over a year or so now since i have used said method, so i have no idea what the script looked like, or where you can get your hands on it... i found it in a howto on these forums

C. as already mentioned... why on earth are you wine'ing uTorrent... there are many many many capable torrent clients for ubuntu/linux natively... Ktorrent and rtorrent are great options (i only wined utorrent for a brief time where the repo version of ktorrent crashed regularly for me... then i discovered rtorrent and never went back)

---

### Post by uberlube on 2008-03-07
Deluge is awesome as well. :)

---

### Post by Nythain on 2008-03-07
Havent played with deluge much, i heard about it back when it came out, but i had discovered rtorrent by that time :(

Anyways, i did a spot of forum searching, and found the original thread i was talking about, and its nto quite how i remember doing it, but i know it works, because i used to do it this way

[http://ubuntuforums.org/showthread.php?t=479095](http://ubuntuforums.org/showthread.php?t=479095)

basically boils down to telling utorrent to autoload torrents in the /tmp directory, then creating a very simple script to launch utorrent, and having firefox run that script upon clicking on a torrent file online... not the greatest method, but if your lazy i guess it works :P

---

### Post by uberlube on 2008-03-07
Ya it almost seems like it would just be easier to start you torrent program and just upload them 1 at a time. Plus it would be a pain in the **** to have to go through all those torrents and specify where they need to be saved all at once. But its all about preference i guess.

---

### Post by whoscheesemine on 2008-03-07
```
If it is it would have to be done from within Utorrents settings.
```

Nah, you can set any file format to open with any terminal command or file execution you'd like.

```
why on earth are you wine'ing uTorrent..
```

Well, to put it simply, I'm too lazy to lookup how to port forward anything else LOL, I did plan on doing that in the future, but I needed to download a certain (LEGAL TO DOWNLOAD:popcorn:) movie in a quick, prompt fashion, and curiosity struck me.

Edit: Well, I know there's a terminal command you can use to launch programs through wine, as I used it to create a launcher for a program once, I had just forgotten it, I'll check that link. thanks

---

### Post by Nythain on 2008-03-07
terminal command would look like
wine /path/to/whatever.exe

like
wine /home/rune/.wine/drive_c/Program\ Files/uTorrent/uTorrent.exe

dont quote me on the exact path, but you get the point

Also, port forwarding is port forwarding... its not different per application, except what port to forward, and in all reality you can set any torrent client to use any port you want... so if you already have utorrents default port forwarded, just tell ktorrent, deluge, rtorrent, etc to use that port and make sure utorrent isnt running... voila, port forwarded and you didnt even have to change a router setting :P

---

### Post by whoscheesemine on 2008-03-07
> **Nythain said:**
> terminal command would look like
wine /path/to/whatever.exe

like
wine /home/rune/.wine/drive_c/Program\ Files/uTorrent/uTorrent.exe

dont quote me on the exact path, but you get the point

Also, port forwarding is port forwarding... its not different per application, except what port to forward, and in all reality you can set any torrent client to use any port you want... so if you already have utorrents default port forwarded, just tell ktorrent, deluge, rtorrent, etc to use that port and make sure utorrent isnt running... voila, port forwarded and you didnt even have to change a router setting :P

Ya know, I considered that, but didn't want to sound like a buffoon assuming that I could set what ever the port ktorrent uses to Utorrent's default port.... looks like I looked like a buffoon anyways! :sad:


Oh, btw thanks for the fresherupper on how to use wine's terminal command, I forgot its just wine then whatever the location is thanks a million.... POST SOLVED!

---

