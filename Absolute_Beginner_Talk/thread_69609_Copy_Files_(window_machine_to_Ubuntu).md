---
title: "Copy Files (window machine to Ubuntu)"
date: 2005-09-27
forum: Absolute Beginner Talk
---

### Post by ProPilot on 2005-09-27
I have a home network. My Ubuntu laptop sees and can access my windows machine "my documents" directory over the network. The problem is that when in the Ubuntu laptop trying to copy a file from the windows machine to my 'home' in the Ubuntu machine the system shows an error saying that the 'home' directory is busy.

How does one copy files, using the Ubuntu machine, from the window machine to the 'home' directory? (hope that was clear?)

Tom

(ps - I was able to open a pdf file located in the windows machine with the Ubuntu pdf reader and then save the file to the Ubuntu 'home')

---

### Post by mlomker on 2005-09-27
> How does one copy files, using the Ubuntu machine, from the window machine to the 'home' directory? (hope that was clear?)


It could be that you just don't have permissions to that directory.  Try copying a file to /tmp as a test.

---

### Post by ProPilot on 2005-09-27
Thanks for the hint. I will have to try later, in the meantime would you tell me how to change the permissions? (Breezy system - works great so far)

Tom

---

### Post by mlomker on 2005-09-27
[QUOTE=ProPilot]Thanks for the hint. I will have to try later, in the meantime would you tell me how to change the permissions? [/quote]

I don't recommend changing the permissions to /home.  You should be able to write under /home/username already.

**sudo chmod 777 /home** would give everyone permissions to the directory.

---

### Post by ProPilot on 2005-09-27
mlomker

thanks - I am the only user on this laptop so no big deal on permissions. I will have to try your suggestions later tonight when I get home.

I also downloaded WinSCP which I will put on the windows machine and see if that works. Back to you later with the results.

Thanks again
Tom

---

### Post by ProPilot on 2005-09-27
I found the problem. The file I wanted to copy from the windows machine wa still hooked somehow to the associated operating program. When I shut down the program I could copy the file over.

Thanks for your help
Tom

---

