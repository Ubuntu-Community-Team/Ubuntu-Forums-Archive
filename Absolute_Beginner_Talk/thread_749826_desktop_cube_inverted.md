---
title: "desktop cube inverted?"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by smooth1975 on 2008-04-08
hey all... just getting started on ubuntu and loving it so far....

though one weird thing happening is that the desktop cube, when enabled, shows me the point of view from inside the cube, not a zoom out cube like i've seen on others desktops...

i hope i explained this right,  and i'm sure it's something small that i'm missing... any ideas?

---

### Post by Crafty Kisses on 2008-04-08
> **smooth1975 said:**
> hey all... just getting started on ubuntu and loving it so far....

though one weird thing happening is that the desktop cube, when enabled, shows me the point of view from inside the cube, not a zoom out cube like i've seen on others desktops...

i hope i explained this right,  and i'm sure it's something small that i'm missing... any ideas?

Sounds weird, do you have 4 desktops?

---

### Post by Joeb454 on 2008-04-08
Have you installed the Compiz Config Settings Manager?

Open up a terminal and type ```
sudo aptitude install compizconfig-settings-manager
```

Then open it up from System>Preferences :)

I think the desktop size is somewhere under "General" make sure that is set to 4 to allow you to get the cube :)

---

### Post by smooth1975 on 2008-04-08
yes i do... strage eh?

---

### Post by smooth1975 on 2008-04-08
> **Joeb454 said:**
> Have you installed the Compiz Config Settings Manager?

Open up a terminal and type ```
sudo aptitude install compizconfig-settings-manager
```

Then open it up from System>Preferences :)

I think the desktop size is somewhere under "General" make sure that is set to 4 to allow you to get the cube :)

yes i already had four desktops... i can spin the cube around between the 4, and it is still a cube... i'm just trapped on the inside of it.

odd

---

### Post by Crafty Kisses on 2008-04-08
> **smooth1975 said:**
> yes i already had four desktops... i can spin the cube around between the 4, and it is still a cube... i'm just trapped on the inside of it.

odd

Do you have desktop reflection enabled?

---

### Post by por100pre1 on 2008-04-08
In **System> Preferences> Advanced Desktop Effects Settings**:

Click **Desktop Cube**,

Click the **Behavior** Tab,

Uncheck **Inside Cube**.

If you don't have the **Advanced Desktop Effects Settings** program; install it like this:
Copy, paste and ENTER this command in Terminal (**Applications> Accesories> Terminal**):

```
sudo apt-get install compizconfig-settings-manager
```

---

### Post by doorknob60 on 2008-04-08
Go into the Rotate Cube plugin options in the Compiz config program, and there's an option in there for Inverted Cube, disable it :)

EDIT: dangit too late :(

---

### Post by smooth1975 on 2008-04-08
> **por100pre1 said:**
> In **System> Preferences> Advanced Desktop Effects Settings**:

Click **Desktop Cube**,

Click the **Behavior** Tab,

Uncheck **Inside Cube**.

If you don't have the **Advanced Desktop Effects Settings** program; install it like this:
Copy, paste and ENTER this command in Terminal (**Applications> Accesories> Terminal**):

```
sudo apt-get install compizconfig-settings-manager
```

ahhhhh problem solved.... thanks so much.... no one ever accused me of being stephen hawking!

---

### Post by por100pre1 on 2008-04-08
> **smooth1975 said:**
> ahhhhh problem solved.... thanks so much.... no one ever accused me of being stephen hawking!

I don't know who's Stephen Hawking, I just wanted to make the answer available to whoever may need it anytime!

---

### Post by Joeb454 on 2008-04-08
**por100pre1** If you want to read about Stephen Hawking, [check out Wikipedia]("http://en.wikipedia.org/wiki/Stephen_Hawking")

---

### Post by por100pre1 on 2008-04-08
> **Joeb454 said:**
> **por100pre1** If you want to read about Stephen Hawking, [check out Wikipedia]("http://en.wikipedia.org/wiki/Stephen_Hawking")

Thanks. :)

---

