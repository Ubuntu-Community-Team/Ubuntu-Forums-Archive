---
title: "How to stop nm-applet at every login?"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by orangemoose on 2007-07-12
[http://ubuntuforums.org/archive/index.php/t-187874.html](http://ubuntuforums.org/archive/index.php/t-187874.html)

I tried to follow the above link, but I don't trust my noob skills. 
Is there a menu driven solution to stopping the nm-key that I 
might have a chance of succeeding at?

Thank you.

---

### Post by Papi-KB7VGW on 2007-07-12
Why would you want to bypass the keyring?  It holds you wep/wpa codes

---

### Post by orangemoose on 2007-07-12
Sorry, I misspoke.

I meant to say: How can I unlock the pass phrase so I don't have to enter it every time I restart?

---

### Post by corney91 on 2007-07-12
I used this tutorial: [http://ubuntuforums.org/showthread.php?t=192281.]("http://ubuntuforums.org/showthread.php?t=192281")
I think it is essentially the same thing but easier to read. It's relatively straightforward but if you need a section in any more depth just ask.

Make sure you have the needed packages:
```
sudo aptitude install build-essential libtool libglib2.0-dev libgnome-keyring-dev libpam0g-dev
```

---

### Post by orangemoose on 2007-07-15
make  install-data-hook
make[3]: Entering directory `/home/allen/Desktop/pam_keyring-0.0.8/src'
( \
                cd /usr//..//lib/security && \
                ln -s pam_keyring.so pam_keyring_auth.so && \
                ln -s pam_keyring.so pam_keyring_session.so \
        )
ln: creating symbolic link `pam_keyring_auth.so' to `pam_keyring.so': File exists
make[3]: *** [install-data-hook] Error 1
make[3]: Leaving directory `/home/allen/Desktop/pam_keyring-0.0.8/src'
make[2]: *** [install-data-am] Error 2
make[2]: Leaving directory `/home/allen/Desktop/pam_keyring-0.0.8/src'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/allen/Desktop/pam_keyring-0.0.8/src'
make: *** [install-recursive] Error 1

Above is the ouput from sudo make install

I proceeded anyways to add the lines to the file, reboot, but I am still being prompted for my password.

I tried to find pam in add/remove and it is not there.

Can you help me put the pieces together.

Thanks.

---

### Post by corney91 on 2007-07-17
> **orangemoose said:**
> make  install-data-hook
make[3]: Entering directory `/home/allen/Desktop/pam_keyring-0.0.8/src'
( \
                cd /usr//..//lib/security && \
                ln -s pam_keyring.so pam_keyring_auth.so && \
                ln -s pam_keyring.so pam_keyring_session.so \
        )
ln: creating symbolic link `pam_keyring_auth.so' to `pam_keyring.so': File exists
make[3]: *** [install-data-hook] Error 1
make[3]: Leaving directory `/home/allen/Desktop/pam_keyring-0.0.8/src'
make[2]: *** [install-data-am] Error 2
make[2]: Leaving directory `/home/allen/Desktop/pam_keyring-0.0.8/src'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/allen/Desktop/pam_keyring-0.0.8/src'
make: *** [install-recursive] Error 1

Above is the ouput from sudo make install

I proceeded anyways to add the lines to the file, reboot, but I am still being prompted for my password.

I tried to find pam in add/remove and it is not there.

Can you help me put the pieces together.

Thanks.

Don't know whats happened here, apparently pam_keyring already exists, so you might have to delete it. But I'd suggest trying the .deb file on post #6. That should be easier.

---

