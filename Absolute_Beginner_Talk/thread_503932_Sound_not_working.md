---
title: "Sound not working"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by Error47 on 2007-07-18
It was working a few days ago. Right now sound isn't playing from any anything. Works fine in windows though. I have been recently plugging in my usb headset to use with skype, but I dont know if that had anything to do with this.

---

### Post by AlexenderReez on 2007-07-18
maybe this can help-->

> [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by Error47 on 2007-07-18
Wow, all that complication just for sound??

---

### Post by AlexenderReez on 2007-07-18
check this please-->

> [http://ubuntuforums.org/showpost.php?p=3040208&postcount=8](http://ubuntuforums.org/showpost.php?p=3040208&postcount=8)

---

### Post by Hobo Joe on 2007-07-18
```

asoundconf list
sudo asoundconf set-default-card cmedia (or whatever the card is called)

```

---

### Post by wolfen69 on 2007-07-18
is it desktop? laptop? what soundcard?

---

### Post by Error47 on 2007-07-19
Desktop with ICH5. I dont what ICH5 is but it used to work when I set it to that. I have an hp pavillion a250n. I dont know what soundcard....

---

### Post by steve.horsley on 2007-07-19
Double-click the speaker icon to get the mixer panel up. Then edit the preferences, enable every slider there and try them all. It worked for me last week.

---

### Post by Error47 on 2007-07-21
No, still no sound.

---

### Post by AlexenderReez on 2007-07-21
have you enable all sound system..?if not,enter in terminal

> gnome-volume-control

enable all....if you are using sound card,please consult with its web ...or search howto about your sound card...

:)

---

