---
title: "Few quick questions"
date: 2006-08-02
forum: Absolute Beginner Talk
---

### Post by xander848 on 2006-08-02
1. Do I ever need to defragment my ubuntu hdd like in windows?

2. Is there a way to input commands into the terminal automatically? For example if i wanted want to enter the commands:
cd ~/wpa
tar -zxvf ipw2100-1.2.1.tgz
cd ipw2100-1.2.1
sudo sh remove-old
make
sudo make install

Can i enter them all at once and have them be executed one after the other?

Thanks!

---

### Post by %hMa@?b&lt;C on 2006-08-02
you never need to defrag, isnt ext3 great? 
you can make a shell script to do that (the second question) If you need help, I can help with that.

---

### Post by xander848 on 2006-08-02
Yeah i did a quick look on google for shell script and got confused...A little help on how to make it would be great.

---

### Post by Tomosaur on 2006-08-02
Put this into a file called myscript.sh
```

#!/bin/bash
cd ~/wpa
tar -zxvf ipw2100-1.2.1.tgz
cd ipw2100-1.2.1
sh remove-old
make
make install

```

Then to run it, type 'sudo sh myscript.sh'

---

