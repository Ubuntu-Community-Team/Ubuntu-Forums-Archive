---
title: "No root login?"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by koganinja89 on 2007-07-22
Is it possible for me to hack Dumb Ubuntu into letting me log in as root from the login window?

---

### Post by mikewhatever on 2007-07-22
Boot into recovery mode and you'll be root.

---

### Post by bernied on 2007-07-22
Yes it is.
But I don't think that it is Ubuntu that is the dumb one here.

There are so many reasons not to do this, and probably a thousand ways to do what you want without doing this (like that suggested by mikewhatever above). So, please don't do it. But having said that, I don't believe in witholding information because I think I know better. So have fun.

First you would enable the root account - just give it a password. ```
sudo passwd
```
Then you would allow root logins in gdm. ```
gksu gedit /edt/X11/gdm/gdm.conf
```You are looking for the line that says 'AllowRoot=false'. You need to change that.

---

### Post by koganinja89 on 2007-07-22
> **bernied said:**
> Yes it is.
But I don't think that it is Ubuntu that is the dumb one here.

There are so many reasons not to do this, and probably a thousand ways to do what you want without doing this (like that suggested by mikewhatever above). So, please don't do it. But having said that, I don't believe in witholding information because I think I know better. So have fun.

First you would enable the root account - just give it a password. ```
sudo passwd
```
Then you would allow root logins in gdm. ```
gksu gedit /edt/X11/gdm/gdm.conf
```You are looking for the line that says 'AllowRoot=false'. You need to change that.

Sorry I am soooooo dumb, I mean I already tried every option in the settings and stuff did you honestly explect to just think of that all on my own. I don't have the internet and I am not a noob, just unfamiliar with gnome thats all, the last time I had gnome was back in the actual "Mandrake" day before it was discontinued.

---

### Post by Tmi on 2007-07-22
> **koganinja89 said:**
> Sorry I am soooooo dumb, I mean I already tried every option in the settings and stuff did you honestly explect to just think of that all on my own. I don't have the internet and I am not a noob, just unfamiliar with gnome thats all, the last time I had gnome was back in the actual "Mandrake" day before it was discontinued.

He didn't mean that you were dumb for not knowing how to enable root. He was referring to that it is a risky thing, and thus a bit dumb, to enable the root account.

---

### Post by koganinja89 on 2007-07-22
My bad sry

---

### Post by Tmi on 2007-07-22
But anyway, since the message was misunderstood, let me re-emphasize that if you enable the root account you should know what you are doing. It's very recommended that you use sudo instead.

---

### Post by bernied on 2007-07-22
> **Tmi said:**
> He didn't mean that you were dumb for not knowing how to enable root. He was referring to that it is a risky thing, and thus a bit dumb, to enable the root account.Yes, that is what I meant. And I apologise if I was rude.

---

