---
title: "Dialup woes"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by Goregamod on 2007-03-25
After downloading and installing the intel 536 drivers from the dialupmodemhowto, I
A.) Can't figure out which port my modem is in, and
B.) Can't figure out how to actually connect.

Any help would be greatly appreciated.
I've got no idea what information to provide or what to say.

---

### Post by Bachstelze on 2007-03-25
```
sudo wvdialconf /etc/wvdial.conf
```

should autodetect your modem, if it's properly recognized.

---

### Post by Goregamod on 2007-03-25
I'll boot back over to ubuntu and give that a try, thanks.
UPDATE: I tried it, it gave me a 'Sorry, no modem was detected' error. Any other suggestions? I appreciate the help.

---

### Post by dstew on 2007-03-25
Enter on the command line:

sudo modprobe Intel536

If it gives you a "FATAL" error message, you have not compiled the driver correctly.

---

### Post by Goregamod on 2007-03-25
I've compiled the driver correctly.

---

### Post by dstew on 2007-03-25
What is the output of the command?

---

### Post by Goregamod on 2007-03-25
None. It gives me another line for input.

---

### Post by Bachstelze on 2007-03-25
Now that you've loaded the module, try running wvdialconf again :)

---

### Post by dstew on 2007-03-25
Do you see the modem name in the /dev directory?

/dev/536ep0

---

### Post by Goregamod on 2007-03-25
> **HymnToLife said:**
> Now that you've loaded the module, try running wvdialconf again :)

Same thing.
[quote=dstew]Do you see the modem name in the /dev directory?

/dev/536ep0[/quote]
Yes.

---

