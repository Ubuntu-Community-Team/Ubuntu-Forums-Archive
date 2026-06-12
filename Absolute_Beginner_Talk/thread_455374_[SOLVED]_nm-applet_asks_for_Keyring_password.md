---
title: "[SOLVED] nm-applet asks for Keyring password"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by Inxsible on 2007-05-26
Ever since I added WPA-Personal security to my network, nm-applet has started asking me the keyring password. I didn't even know that I had set one, but apparently its the same as the passphrase for my WPA.

On searching through the forums, I found this  [http://ubuntuforums.org/showthread.php?t=187874](http://ubuntuforums.org/showthread.php?t=187874)

but before I make any changes, I wanted to know why this is occurring in the first place. Even without entering the keyring password or even on denying it, my internet connection still works. So what is the keyring exactly ?

Thanks in advance !

---

### Post by Mazen on 2007-05-26
i have a keyring password too, but mine is not the same as the key, well it was like that at first but i changed it to a simple word, so i guess it's just instead of entering your long 128-bit key everytime when you're in Roaming mode...but if u say that u internet still works....well that's weird...i'm not on my ubuntu machine right now but i gues that's how it goes i just choose the connection and it has and assigned keyring for it!
hope i made sense here!! lol

---

### Post by seetho on 2007-05-26
A keyring stores all your passwords.  You may want to connect to different wireless networks with different passwords automatically without having to key in the WPA or WEP passphrase every single time, so they are all stored in a keyring that nm-applet (network manager applet) needs to access.  This keyring is protected by a password that you assign one time.  You should use a different password from the one you use for your wireless security.

If you want to change it, just go to the Keyring Manager and delete the keyring.  You'll be asked to assign a password next time you use it.

---

