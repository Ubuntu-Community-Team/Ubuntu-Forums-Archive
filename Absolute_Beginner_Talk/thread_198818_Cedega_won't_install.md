---
title: "Cedega won't install"
date: 2006-06-17
forum: Absolute Beginner Talk
---

### Post by skale on 2006-06-17
I'm trying to install Cedega, and the damned thing won't work. 
> To install Cedega 5.1.3:

1. First extract cedega-5.1.tar.gz into the current directory.
2. In a root shell change directory to where you extracted the files.
3. cp etc/* /etc/
4. cp opt/* /opt/
5. cp usr/* /usr/
6. Now run 'cedega' as your normal user.
7. Follow instructions but do not try to update via the internet
just leave all the user info blank.
8. Once in the actual Cedega interface click TransGaming->Install Local Update
9. Pick the cedega-engine-5.1.3-local-update.i386.cpkg file.
10. Accept the licence agreement.
11. If there were no errors you should be back in the interface.
11b. If there are errors your download is corrupt or you have spaces in the path to the file (cedega does not like spaces when updating.)
12. Restart cedega (still as your normal user) and it should now work.

Enjoy!

I extracted everything and did everything right until steps 3,4, and 5.
I type:
> sudo cp etc/* /etc/
and it says:
> cp: omitting directory `etc/X11'

---

### Post by Kilz on 2006-06-17
[QUOTE=skale]I'm trying to install Cedega, and the damned thing won't work. 

I extracted everything and did everything right until steps 3,4, and 5.
I type:

and it says:[/QUOTE]
Why not make it easy, use the .deb file to install cedega. It should be available from transgaming.

---

### Post by croak77 on 2006-06-17
Buy a subscription at transgaming,com and then you can download a .deb file.

---

