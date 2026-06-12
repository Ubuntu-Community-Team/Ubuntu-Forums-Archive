---
title: "Thunderbird messages"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by Niloc on 2007-04-10
I have Ubuntu 6.1 on my laptop and my desktop. I want to transfer the desktop eMails to the laptop. Thunderbird has an 'import' function but I cannot find any 'export' command. I assume I must copy the message file across but what is the name of the file and where do I find it?

---

### Post by justleen on 2007-04-10
the message are stored in ~/.mozzila-thunderbird/<some number here/*
the some numer is a generated folder name

what i do, is launch thunderbird (cancel the wizard) so it creates the directory.
close it again, then copy the contents of the some number folder.
Dont copy the folder itself though, that wont work.

---

### Post by igknighted on 2007-04-10
> **Niloc said:**
> I have Ubuntu 6.1 on my laptop and my desktop. I want to transfer the desktop eMails to the laptop. Thunderbird has an 'import' function but I cannot find any 'export' command. I assume I must copy the message file across but what is the name of the file and where do I find it?

If you copy the .thunderbird folder from your home folder to the laptops the settings (and messages?) should come with it I believe.  You might try that.  Are you using a pop3 server or imap?  If you have an imap server you could re-download them, but with pop3 you'll have to manually move them.

---

### Post by justleen on 2007-04-10
in my experience, it wont work, copying the whole .mozzila-thunderbird folder..

one would expect it to work since you copy the profiles.ini as wel.. but that kite just doenst fly...

---

### Post by Niloc on 2007-04-10
Thanks, I was also going to ask if it is possible to get gMail to mark old messages  so they are re-sent to my computer next time it logs in to get mail. I am using the POP protocol.

Thanks,
Colin

---

### Post by justleen on 2007-04-10
i think you have to enable that on the Gmail prefs..

---

### Post by sam81 on 2007-04-10
> **justleen said:**
> in my experience, it wont work, copying the whole .mozzila-thunderbird folder..

one would expect it to work since you copy the profiles.ini as wel.. but that kite just doenst fly...


I've done that quite a few times, and it usually works. Only problem once when I had installed a custom extension, it wouldn't copy a certain file, I think because it was a link rather than a normal file. Apart from that worked flawlessy, and you get all account settings as well

---

