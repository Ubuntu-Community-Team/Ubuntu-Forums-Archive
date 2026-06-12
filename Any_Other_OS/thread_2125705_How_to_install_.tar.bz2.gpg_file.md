---
title: "How to install .tar.bz2.gpg file"
date: 2013-03-14
forum: Any Other OS
---

### Post by thebiz2011 on 2013-03-14
I'm running backtrack 5r3. I downloaded the Rover mapping software and this is the file name /root/Desktop/linux-x86-ROVER-4.3-gcc336-29oct2012.tar.bz2.gpg. I ran #sudo apt-get install gpa.  I then ran #gpg --decrypt linux-x86-ROVER-4.4-gcc336-29oct2012.tar.bz2.gpg.  This is the response gpg: can't open `linux-x86-ROVER-4.4-gcc336-29oct2012.tar.bz2.gpg'
gpg: decrypt_message failed: file open error

I don't know how to complete the install on .gpg files.  I have only been using ubuntu for 3 days now so please be patient with me. 

Thank you in advance.

---

### Post by papibe on 2013-03-14
Thread moved to **Other OS/Distro Talk**.

---

### Post by schragge on 2013-03-15
Looks like either permissions/ownership of the file are wrong or you made a typo in the file name or the file is simply not there. Were you running gpg from */root/Desktop* as root? And why the file is in */root/Desktop* of all places? I hope you aren't running your GUI session as root, are you?

---

### Post by Lars Noodén on 2013-03-15
The .gpg file should contain the PGP signature for the .tar.bz2 file.  So to do an installation you need both files, the data file (.tar.bz2) and the signature (.gpg) to verify the integrity and authenticity of the data file.  Where did you download these from?   It's better to use the repository if you can.

PS.  The path /root/Desktop implies that you might be running X as root.  If you are, we can help you find a way to stop.  It's dangerous to do so.

---

### Post by schragge on 2013-03-15
> **Lars Noodén said:**
> The .gpg file should contain the PGP signature for the .tar.bz2 file.  So to do an installation you need both files, the data file (.tar.bz2) and the signature (.gpg) to verify the integrity and authenticity of the data file.Nope. In this case the gpg message would be
```

Detached signature.
Please enter name of data file:

```

---

