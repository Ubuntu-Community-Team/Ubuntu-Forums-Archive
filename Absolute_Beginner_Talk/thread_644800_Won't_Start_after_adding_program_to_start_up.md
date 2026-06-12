---
title: "Won't Start after adding program to start up"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by n5bail on 2007-12-19
I added twonkymedia server to the start up, restarted my computer and now it's stuck at "Starting server." I cannot boot the gui it's just stuck at "starting server." If anyone could help me remove the program from start up in failsafe mode it would be great.

---

### Post by spiderbatdad on 2007-12-19
not sure if i can help, but i'll try. Can you get to the command line interface (terminal) from the sart-up? try ctrl-alt-f1. If you can get a terminal try```
sudo apt-get remove --purge twonkymedia-server
```

---

### Post by p_quarles on 2007-12-19
Or, if the above fails, you can use Recovery Mode (from the GRUB menu) to get a root command line. Run the command mentioned in the post above this one, but without "sudo."

---

### Post by n5bail on 2007-12-19
Neither worked for me, but thanks for the help.

it's a .sh file that i extracted to the /etc/init.c folder. I'm pretty sure it's not starting because it's a 32 bit version running in amd64. If anyone know's how to stop it when I start ubuntu that would help. I ran a command for it to start when ubuntu is booted and now I can't get ubuntu to boot.

---

### Post by RomeReactor on 2007-12-19
Hi. Were you able to boot in Recovery Mode? if so, try deleting the .sh file:
```
rm /etc/init.c/FILENAME.sh
```

If that doesn't work, or you're unable to go into Recovery Mode, maybe running the Live CD and mounting the HD will let you get rid of the script.

---

### Post by p_quarles on 2007-12-19
Do you mean the /etc/init.d folder? That's the only one that I know of. 

And, just because a lot of people -- myself included -- have warnings in our signatures about the "rm" command, I'll go ahead and confirm RomeReactor's specific instructions here are correct (except it's init.d, not init.c) and safe. Just be careful that you type the exact name of the file you want to delete If you'd still rather avoid it, for whatever reason, you can also simply prevent the file from executing, by running this in recovery mode:
```
chmod 660 /etc/init.d/FILENAME.sh
```
That will change it into a non-executable file, and it won't try to load at startup.

---

