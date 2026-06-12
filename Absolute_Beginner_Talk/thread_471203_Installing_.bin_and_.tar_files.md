---
title: "Installing .bin and .tar files?"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by toecutter on 2007-06-11
I'm still at a loss as to how to install these types of files. Call me blind, but I couldn't find info on the Ubuntu Guide page.

Specifically, I'm trying to install official RealPlayer support and they supply it in a .bin format but every now and then I come across files from websites that can't be installed by Automatix or Add/Remove. 

Can anyone give me a quick primer or point me to a website with this basic info? Cheers :)

---

### Post by Bachstelze on 2007-06-11
Those files can contain different type of software so it's basically impossible to give general instructions. Installation instructions should be provided with the software.

---

### Post by taurus on 2007-06-11
Applications -> Accessories -> Terminal
```
cd ~/Desktop
chmod 755 **filename.bin**
sudo ./**filename.bin**
```

[http://monkeyblog.org/ubuntu/installing/#source](http://monkeyblog.org/ubuntu/installing/#source)

---

### Post by RelativelyQuantum on 2007-06-11
I'm not certain weather this would apply, but you could try searching for your "INSTALL" file in your home directory. That might give further insight...

---

### Post by toecutter on 2007-06-11
Cheers guys :)

For RealPlayer 10 Gold, Taurus's instructions were spot on. Thanks for the link as well, now I know what the file extensions are for :)

---

### Post by Nezing on 2007-06-12
Oh dear.I too followed taurus's instructions to load Real Player 10,and it just does zip.Terminal says "no such file exits",and yet,there it is,sitting on my desktop.I even went to the Ubuntu info page,where the instructions for installing bin files are different?
Thinking of purging Ubuntu at this rate,and going back to you know what...](*,)
Only kidding...just a little fed up.

---

### Post by taurus on 2007-06-12
What's the name of the file then?

```
cd ~/Desktop
ls -la
```

---

### Post by Nezing on 2007-06-12
RealPlayer10GOLD.bin is sitting on my desktop.Nope,still doing zip in Terminal.Just says command not found.:(

---

### Post by taurus on 2007-06-12
Did you really download the .bin instead of the .zip file?

```
cd ~/Desktop
chmod 755 RealPlayer10GOLD.bin
sudo ./RealPlayer10GOLD.bin
```

---

### Post by Nezing on 2007-06-12
:popcorn:

Hooray.After complaining,Terminal has just come up with the goods,and installed Real Player 10.There is the link,under Applications->Sound&Video->Real Player :D
Yes it was a bin file,and I was copying all commands,but no-can-do.But your last "copy and paste",worked.Thanx for your patience taurus.

---

