---
title: "A GIMP add-in Installation? (brief How-To needed)"
date: 2006-09-03
forum: Absolute Beginner Talk
---

### Post by Alias- Human on 2006-09-03
I have a file; gimp-texturize-2.0.tgz on my desktop. I realy don't know how to get it into GIMP the way it is suposed to be.

Perhaps I'm being a little bone-headed but this is my very first attempt at installing a packaged file so I am a little unclear about the instructions.

I tried to unpack the file and got another file on my desktop. I looked inside it and found a README. It said to "cd" to gimp (I think) and type in the terminal;
./configure
make
make install

Ok, I'm sure that is simple enough. I know how to get the 'Terminal', I've actualy used it for one other thing.
I get that I must type in to it;
 "cd" and then some file name (I don't know Which gimp file I should type in though)

Do I type in; ./configure gimp-texturize-2.0.tgz
and then; make gimp-texturize-2.0.tgz
then; make install gimp-texturize-2.0.tgz
or does it know that this file is being refered to in all succesive comands?

Can somebody point me to some Very clear step-by-step instructions for this, I tried to look it up in the documentation but that didn't tell, (or, I didn't know where in there to look). I'm sure that this is the easiest thing in the world but for some reason I just ain't getting it at the moment.

Thanks,
AHDRL

---

### Post by meng on 2006-09-03
To install from source:
1) Unpack the file
2) cd to the directory where the file was unpacked (in your case, to gimp-texturize-2.0)
3) ./configure
4) make
5) sudo make install

The commands don't have anything extra on the end.

---

### Post by Perfect Storm on 2006-09-03
```
cd /into/the/extracted/gimp-texturize
./configure
make 
sudo make install
```

Watch whe ./configure rolls by. It tells you if you're missing something.

---

### Post by Alias- Human on 2006-09-03
Right On Folks, Thanks!

---

