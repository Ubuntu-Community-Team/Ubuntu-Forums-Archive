---
title: "[SOLVED] Adobe flash in ubuntu install"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by EnergySamus on 2007-12-22
Hello!
I know that the post about Adobe flash has been posted a hundred times, but they are too complicated for me.
How do you install Adobe flash player?
I do not know how to use the terminal very well.:confused:

Thanks
EnergySamus

---

### Post by LaRoza on 2007-12-22
In Gutsy:

Go to System->Administration->Software Sources

Go under "Upates" check the box for "Pre Release...."

Run these commands:

```

sudo apt-get update

```

```

sudo aptitude install flashplugin-nonfree

```

You can uncheck the box then, if you don't want those updates.

---

### Post by EnergySamus on 2007-12-22
Thank you!



EnergySamus

---

### Post by Sef on 2007-12-22
Also Applications > Add/Remove > change the top right box to :all available applications" > in Search type Adobe.

---

### Post by fedex1993 on 2007-12-22
hmm i tried yours laroza and i still cant seem to get mine to work after chaning that

---

