---
title: "How to run a BIN file?"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by mjpatey on 2007-02-13
Hi, all-

I've been away from Ubuntu for a while, and I'm back.  :-)

I'm embarrassed to ask... I can't remember what to do with a BIN file in order to make it executable.  My brain seems to be squirting out random things like chmod and ./ and sh... things like that, some of which are hopefully close to the commands I need to make this happen.

Can somebody refresh my garbled memory?

Thanks!

-Mark

---

### Post by igknighted on 2007-02-13
./filename.bin should do the trick, run it with sudo if its an installer.

EDIT: to make it executable, right click it, go to permissions and then click the option 'make executable' so it is on.

---

### Post by Motoxrdude on 2007-02-13
cd /(where file is)
chmod 775 (name of file)
./(name of file)
Enjoy :)

---

### Post by mjpatey on 2007-02-13
Motoxrdude,

Thanks, that did the trick!  It's all coming back to me now...

---

### Post by Motoxrdude on 2007-02-14
Heh, no problem. I just learned how to run bins just last week so i am more then glad to help others.

---

### Post by nalioth on 2007-02-14
I guess this bin wasn't an image file.

---

