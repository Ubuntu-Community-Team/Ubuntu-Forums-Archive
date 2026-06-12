---
title: "vive error....."
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by kamitsukai on 2007-11-17
i keep getting an error when encoding with vive :(

---

### Post by skymera on 2007-11-17
hmm try it with sudo?

and nice theme :)

---

### Post by kamitsukai on 2007-11-17
how do i try it with sudo?

thnx, yer i like it to :P

---

### Post by jaybombalous on 2007-11-17
bash says it doesn't understand this ' !" ' Remove the '!' and try again.

Or u could try putting up a '/' in front of the '!' but I would first try removing the '!'.


```
bash : !" : Event not found <--- this is the error, so fix it and remove the ! since u need the " to close the beginning of the "
```

---

### Post by kamitsukai on 2007-11-17
yer but im a noob thats why i chose a gui frontend so i didnt have do do any of that :P so how would i do that?

---

### Post by jaybombalous on 2007-11-17
So there is no where u typed in "Encoded in ubuntu!" because thats why bash is complaining, because of the exclamation point (!).


U could do as the other guy said and try sudo, to do that u would need to give the gui frontend sudo permissions. U do this by going to a terminal and typing in 

```
sudo vive
```


this opens vive with root permissions so u can run everything in vive as root.


edit: check all the options in the GUI  for the phrase. "Encoded in ubuntu!" and delete the exclamation point. This isn't that hard, u have to search and look for the phrase and delete one character. I have never used vive but I am sure some place there is an option, maybe not, but either way thats your solution. I can't do it for you...

---

### Post by jaybombalous on 2007-11-17
why u so stuck on a frontend? The phrase u see in the terminal is no more then a text input box in a GUI frontend. U still have to type in text no matter which way u use it. A flag for the terminal (IE. -w -l -r etc...) are check boxes in the frontend. U still have to check them as well.

---

