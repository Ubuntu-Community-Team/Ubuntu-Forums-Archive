---
title: "Video edit ?"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by thedoors on 2007-05-09
What program should i use if i want to edit a video ?
Specifically, i have a 25minutes video and i want to split it in part of 10 (10, 10, 5)
So i can upload it on youtube.com

thanks in advance

---

### Post by starcraft.man on 2007-05-09
You can use Kino to do this, some people find it more difficult with the gui. However, I and a lot of people seem to prefer Cinelerra.

Easy to install:

Open the terminal (Applications > Accessories > Terminal)

Open the sources list:
```

gksudo gedit /etc/apt/sources.list

```

Then add one of the following lines to it:

- i686:
deb [http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/i686/](http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/i686/) ./
- athlonxp:
deb [http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/athlonxp/](http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/athlonxp/) ./
- pentium4:
deb [http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/pentium4/](http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/pentium4/) ./

Assuming your using a regular CPU you probably want penium 4, unless you know your not using that.

Then, save and close it.

Type these in terminal :

```
sudo aptitude update
```

```
sudo aptitude install cinelerra
```

Then open it from applications > multimedia > Cinelerra.

Voila! Great video and audio program in a few minutes :)

---

