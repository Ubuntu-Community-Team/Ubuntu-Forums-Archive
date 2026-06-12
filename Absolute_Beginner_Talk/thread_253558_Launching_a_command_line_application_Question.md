---
title: "Launching a command line application Question"
date: 2006-09-08
forum: Absolute Beginner Talk
---

### Post by seekyrr on 2006-09-08
When I run **checkgmail** from a terminal it works great and launches an applet in the systray.  If I close the terminal window I ran the command from the checkgmail application closes also.

Is there a way to run a commandline application like this and close the original terminal but not the application?

Thanks

Seek.

---

### Post by PingunZ on 2006-09-08
Do ALT+F2 --> checkgmail
Its just a program laucher.
Like in windows ( Windows + R )

Cheers

---

### Post by bulldog on 2006-09-08
Yes there is.
Right click on your panel and choose add to panel.
Then choose start application [I think,I'm running a Dutch version]

You should have an icon in your panel to put in your app. to start.

---

### Post by Anonii on 2006-09-08
> **seekyrr said:**
> When I run **checkgmail** from a terminal it works great and launches an applet in the systray.  If I close the terminal window I ran the command from the checkgmail application closes also.

Is there a way to run a commandline application like this and close the original terminal but not the application?

Thanks

Seek.
I know that you can do this "checkgmail &" and continue using the terminal while checkgmail is running. I dont know you can close the terminal and make it to run in the background, if its possible.

And of course, as PingunZ proposed you can use the "Run Command" , with Alt+F2, which is both easy and fast.

---

### Post by IYY on 2006-09-08
The above replies are indeed the best ways to go about what you're trying to do, but to answer your question more directly:

```
nohup <commandname> &
```

is how you launch an app in the terminal without having it closed when the terminal is closed (this is very useful with SSH connections, where you might want to start a download and then log out).

---

