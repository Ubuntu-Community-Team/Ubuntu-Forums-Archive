---
title: "Text to Speech"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by Tumpster on 2007-05-08
How can I or what do I need to do to configure Ubuntu so in UT2004 I can utilize the added text to speech? I Know in windows it did it automatcially and I understand we're in ubuntu but I was looking for what I could do to get it on UT2004, I've set up ut2004 to utilize it but it's not going to work if I dont have the proper software for it. Can anyone point me in the right direction?

---

### Post by Skrynesaver on 2007-05-08
Not sure if this is what your looking for but try installing the festival package
```

apt-get install festival

```

---

### Post by Tumpster on 2007-05-08
IT says it's already loaded, how do i activate it?

---

### Post by Skrynesaver on 2007-05-08
```
festival -tts file.txt
```
reads file.txt to you
```
 festival
festival> (SayText "Hi Thumpster, have fun with this")

```
Does what it says ;)[B]
[/B]

---

### Post by Rhubarb on 2007-05-08
UT2004 uses microsoft's inbuilt text to speech engine.
I don't know of any ways you can get UT2004 to use festival without having the UT2004 source code.

I know some games output in-game chat to the terminal, where it should be possible to use festival to speak it all.  It's been a year since I've ran UT2004 in Ubuntu, so I can't remember.

---

