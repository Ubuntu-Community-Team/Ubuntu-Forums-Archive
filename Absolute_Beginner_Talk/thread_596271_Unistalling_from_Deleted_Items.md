---
title: "Unistalling from Deleted Items"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by overandunder on 2007-10-29
Hi

I think I am in the running for idiot of the week with this one!;

Don't ask me how but I managed to download RealPlayer 10 and install it twice inside the Deleted items location, and have tried everything I can think of to delete both copies, but just get messages saying I am not the owner and don't have permissions, yada, yada, yada.  Have tried changing permissions and ownership for the hidden .Trash folder (chmod and chown) and sub directories but nothing happens - it still won't let me get rid of anything.

Have tried getting Synaptic to find them but it draws a blank.  Is there a 'File Nuke' facility where I can search the whole drive and zap any reference to RealPlayer?

I downloaded it as a raw file from Real and installed it via terminal.

Any ideas gratefully received. Could I just re-install Ubuntu ?

Thanks

---

### Post by rowanparker on 2007-10-29
```
sudo rm -rfv ~/.Trash/*folder_name*
```
Post output if it fails.

---

### Post by taurus on 2007-10-29
Is the .Trash in your own $HOME, ~/.Trash?  If it is, what's the output of this command from a terminal?

```
ls -la ~/.Trash
```

---

### Post by overandunder on 2007-10-29
Thanks rowanparker it worked a treat!  Would be really grateful if you could give me a breakdown on the command you described? i.e what do the arguments -rfv provide and the ~ symbol?

Thanks for your reply Taurus, but didn't need it as it worked with rowans' suggestion.

-

---

### Post by rowanparker on 2007-10-29
> **overandunder said:**
> Thanks rowanparker it worked a treat!  Would be really grateful if you could give me a breakdown on the command you described? i.e what do the arguments -rfv provide and the ~ symbol?

Good good :)

Yeah I will: 'sudo rm -rfv ~/.Trash/*folder_name*'
1. 'sudo', run a command as root, I guess you know that one.
2. 'rm', short for remove, does as the title suggests.
3. '-r' means recursive (it will do it for all files and folders inside a directory not just the directory itself).
4. '-f' means force, it will attempt to do it even if it thinks it will fail.
5. '-v' means verbose, it will echo lots of output for us.
6. '~' means /home/*user* and will always point to your $HOME (run: echo $HOME to see where this is).
7. '.Trash' is of course your trash folder.
8. '*folder_name*' is obvious.

Hope that helps.

---

### Post by overandunder on 2007-10-29
Thanks again, spot on.

---

### Post by rowanparker on 2007-10-29
> **overandunder said:**
> Thanks again, spot on.
No worries :)

If there is anything else, just ask.

---

