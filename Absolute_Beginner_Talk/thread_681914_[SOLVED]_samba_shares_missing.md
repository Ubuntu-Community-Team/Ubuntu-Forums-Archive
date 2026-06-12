---
title: "[SOLVED] samba shares missing"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by aBitLater on 2008-01-29
I lost my samba shares somehow.

How can I begin to investigate what went wrong?  They worked fine, til I checked today from a windows machine.

Earlier I added a share to a directory owned by root (/var/www/), and it shows up, but all others are gone.

---

### Post by LRT on 2008-01-29
you can do a few things:

1. if you saved a copy of smb.conf before you added the root share, try going back to that original and then see if you can see the other shares...

2. or, if you didn't save the original smb.conf, then just remove or comment out the root share from the file and see what happens..

3. or, go to your windows machines and try re-mounting the shares that disappeared. 

these are just basic troubleshooting methods... let me know what you've already tried... and we can go from there..

---

