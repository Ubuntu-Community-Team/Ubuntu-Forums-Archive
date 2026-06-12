---
title: "Encrypted Directory Launchers"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by brandg on 2007-04-07
I recently learned how to encrypt/decrypt a directory, which involves mounting the directory with encfs. So, with one line in the Terminal, I can "open" my encrypted directory ( encfs /home/<me>/<encrypted Directory> /home/<me>/<encrypted mountpoint), and with another line in Terminal, I can close it again ( fusermount -u /home/<me>/<encrypted mountpoint>/ ).

So, I want to make this process a little more streamlined. I wanted to find a way to make it happen without going into the Terminal.

I made "launchers" for them, which appear to my MS-centric mind to be like a Windows shortcut. In each launcher, I put the command that I would normally use in the Terminal.

Now, I ran into a problem. The "CloseEncrypted" launcher works fine, but the "OpenEncrypted" launcher does nothing at all. I believe it's because the call to encfs requires a password.

So, to get around the problem, I made a BASH script for it  (OpenEncrypted.sh), and called that from the launcher. I thought that, recognizing it was a BASH script, it might open up the terminal for me, and request the password. However, when I click on that launcher, nothing persists in happening.

I'm obviously very new at Linux, and I don't understand how BASH works all that well, but is there a way for me to tell the terminal to open and load a given script?

---

### Post by chewearn on 2007-04-07
I learnt from another thread about making a password prompt:
[http://ubuntuforums.org/showthread.php?t=380469](http://ubuntuforums.org/showthread.php?t=380469)
Though the script is for Truecrypt, you might be able to adapt it to your purpose.

For example, in the script, the output from the password prompt is piped to the truecrypt program; so, maybe this could work:
gksu -p --message "Please enter your password" | encfs /home/<me>/<encrypted Directory> /home/<me>/<encrypted mountpoint>

---

