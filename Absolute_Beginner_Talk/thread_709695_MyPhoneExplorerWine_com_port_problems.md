---
title: "MyPhoneExplorer/Wine com port problems"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by talvon on 2008-02-27
I'm trying to get the app MyPhoneExplorer to work with WINE by following the instructions here:

[http://www.fjsoft.at/forum/viewtopic.php?t=2838&postdays=0&postorder=asc&start=0&sid=b7263a31c137365b9b386541d5096b88](http://www.fjsoft.at/forum/viewtopic.php?t=2838&postdays=0&postorder=asc&start=0&sid=b7263a31c137365b9b386541d5096b88)

I've successfully registered all the .dlls etc and the program loads, but I can't get it to connect to my phone through USB (I dont have a bluetooth adapter)

It says:

```
:~/$ cd ~/.wine/dosdrive/
:~/.wine/dosdevices$ ln -is /dev/ttyACM0 com1 
```

I don't seem to have a dosdrive folder, and when using the 2nd line it says y/n and when I press yes it doesn't do anything :(

Any help would be appreciated :)

---

