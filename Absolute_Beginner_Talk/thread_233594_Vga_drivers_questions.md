---
title: "Vga drivers questions"
date: 2006-08-10
forum: Absolute Beginner Talk
---

### Post by geokok1981 on 2006-08-10
Ok here goes my list of questions.I have an ATI X700 256mb mobile.

1. I have installed the drivers through the "restricted modules" repo.
So, do I have ATI's official drivers or not (I know they are not the latest version, just asking if they are the official ones).

2. Since I dont want to manually install the new ones, will they be available through the same procedure ("restricted modules") and if yes when? Will they be updated autmatically? (my sources list was made from sourc-o-matic web page with all ubuntu repos activated (main,restricted,commercial,universe,multiverse).

3. I run glxgears -printfps and I get an average of 4650 fps. Is that a good score given that I have a Pentium M 2.0 Ghz, 1024 ram and the vga I mentioned at the begining?

---

### Post by rowanparker on 2006-08-11
1. ```
lspci | grep ATI
``` will list what drivers use ATI.

2. Sorry, don't know.

3. Yes, it's 3 times bigger than mine.


Rowan.

---

