---
title: "Errors with installing programs."
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by kevindubrow on 2007-07-31
Hey, just today I have had some apparent problems with installing programs.

I get this message when I try to update my computer or get a program from Add/Remove Programs: 
"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

If I type ''dpkg --configure -a'' in the terminal I get this message:
"dpkg: requested operation requires superuser privilege"

Any ideas how to fix this problem? Thanks.

---

### Post by wormser on 2007-07-31
You need to put **sudo** in front of the command for root privileges.  This should work for you:

```
sudo dpkg --configure -a
```

Then enter in your password.  More information on [sudo]("https://help.ubuntu.com/community/RootSudo").

---

### Post by ayenack on 2007-07-31
you need to type this in terminal.

sudo dpkg --configure -a

It'll prompt you for a password put in the password you log on with. That's it.

---

### Post by kevindubrow on 2007-07-31
Ok, that appeared to work but now I have a whole mess of new errors.

**When opening up the update service:**
"A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:The package virtualbox needs to be reinstalled, but I can't find an archive for it.'"
[B]
When opening up package manager:[/B]
"E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report."

There is a similar message when running Add/Remove Programs, but now the program wont run so that I can get the error. This obviously has something to do with Virtual Box. I tried installing the program last night, but the installer froze and the computer was running very oddly. I shut down the computer and didn't notice any errors until now. What should I do to get rid of the bits of Virtual box that actually did get installed onto my computer? Thanks again.

--------------------------
Also, I have tried to use the Virtual Box installer, but I get this error:
"The package might be corrupted or you are not allowed to open the file. Check the permissions on the file"

I checked the permissions: Read and write.

---

### Post by Majorix on 2007-07-31
Try this, it will fix it:
```
sudo dpkg --remove --force-remove-reinstreq virtualbox
```

---

### Post by kevindubrow on 2007-07-31
Thanks a lot, you're a life saver. I wish I understood the terminal commands enough to just be able to fix my own problems! Thanks again everyone!

---

