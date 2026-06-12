---
title: "[SOLVED] Learning the terminal...noob question..."
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by e1ektrob0y on 2007-10-26
This is possibly a super noob question so please don't hit me :O 
My goal is to learn to use the terminal for everything and get all the keyboard shortcuts happening so i hardly have to touch my mouse...Anyway i've read a few tutorials on the terminal and its going ok so far except...when i use a terminal to open say, firefox, my "me@me-desktop" disappears and any command i type after that just keeps listing on a new lne and nothing happens...I can open a new tab and me@me-desktop" reappears in that tab, but the previous one becomes useless...Why is this?

It looks like this...
```

ben@ben-desktop:~$ firefox
pidgin
blah
blah'
work damn you...

```

---

### Post by rudeboyskunk on 2007-10-26
It's because you can only run one program in a terminal at a time.  If you type "firefox" into a terminal, that terminal is running firefox until you close firefox.  To run another program, you have to open another terminal.

---

### Post by Orbital75 on 2007-10-26
Here is a great Link that will teach you a good bit.

[http://www.linuxcommand.org](http://www.linuxcommand.org)

---

### Post by evilregis on 2007-10-26
You can run:  firefox &

...and Firefox will open and give you your prompt back to continue working.

---

### Post by llamakc on 2007-10-26
You in no way need to open another terminal.

When you run programs in your $PATH from the command line like `firefox`, you can append an & to it so you get your prompt back.

```

firefox &

```

Should do what you want.

---

### Post by e1ektrob0y on 2007-10-26
> **llamakc said:**
> You in no way need to open another terminal.

When you run programs in your $PATH from the command line like `firefox`, you can append an & to it so you get your prompt back.

```

firefox &

```

Should do what you want.
Sweet, thats exactly what i needed to know thanks:D I have already checked out [http://www.linuxcommand.org]("http://www.linuxcommand.org") its great...

---

