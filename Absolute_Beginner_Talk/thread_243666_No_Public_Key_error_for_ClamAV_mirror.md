---
title: "No Public Key error for ClamAV mirror"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by oss_monkey on 2006-08-25
Greetings. May Ubuntu be with you. ;)

I tried updating my ClamAV installation by following the instructions at the ClamAV website. I inserted a mirror in my /etc/apt/sources.list, from the list given at [http://www.clamav.net/binary.html#pagestart](http://www.clamav.net/binary.html#pagestart)

When I ran "sudo aptitude update", I get the following error at the end of the updating process:

```
W: GPG error: http://mirror.free.net.ph sarge/volatile Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7EF7FFF4276981F4
W: You may want to run apt-get update to correct these problems
```

I tried using "sudo apt-get update", I still got the same error message. Anyone have an idea what's wrong?


TIA.

---

### Post by Cone on 2006-08-25
No clue what you're doing wrong, but you can get a Ubuntu .deb package from the Universe repositories.

Just "sudo apt-get install clamav" for manual use
OR
"sudo apt-get install clamav-daemon"

Source and more info about using ClamAV if needed: [https://help.ubuntu.com/community/ClamAV](https://help.ubuntu.com/community/ClamAV)

:)

~Cone

---

### Post by rtimai on 2008-04-05
The original inquirer has probably already resolved the No Public Key issue, but for other noobs like me, I thought this tip might help.

 When you add a new repository, you should also look for an Public Key authentication link for that repository. Usually you will be able to find a link to the key which will display in the browser as an ASCII (*.asc) plain text file. Save the page without renaming it to a easily-found directory under your home directory. When you've done so, start the Synaptic Package Manager, click on Settings, Repository, and under the Authentication tab, click on the Add button, navigate to the *.asc file you just saved, and click Open to add the Public Key. You will then see it listed in the Trusted Software Providers list. Then you will no longer see a No Public Key error warning.

You may also find command line instructions for retrieving and adding the key to your repositories data. 

JFYI, I found that this error did not prevent actual access to the repository, however. I added the etch/volatile repository, saw the Public Key error when I "reloaded" the Package Manager, but was able to update my ClamAV definitions anyway. I fixed the public key error afterwards.

---

