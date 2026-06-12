---
title: "[SOLVED] Truecrypt Volume Mounting problems"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by fmbugdadi on 2007-12-10
I got through creating a key, and creating a virtual volume without a problem, however, I am having a problem with volume mapping. When I create a key, and the virtual volume, it does so, by default, in my root directory (/home/martin), The command for mapping a volume is "truecrypt /root/home.txt -k /root/key"   <-- where it says root, I am replacing this with my root directory, (/home/martin/). Also, at the end, I am adding the ".txt" extension to "key" because this appears to be an error in the documentation. the key created in my root directory has a "txt" extestion, and if I don't add it to the command, it says "command not found". After I enter "truecrypt /home/martin/home.txt -k /home/martin/key.txt", it asks me for password for /home/martin/home.txt, which I entered and i get "Incorrect password and/or keyfile(s) or not a TrueCrypt volume". I have tried this repeatedly. I even deleted the keys and volumes and created new ones. I was also reading, that truecrypt needs a program called "DMSETUP" for volume mapping. I checked on the Synaptic package manager, and it is already installed". Does anyone see anything obvious I might be doing wrong? Any help would be greatly appreciated....

---

### Post by fmbugdadi on 2007-12-11
Well guys, I figured out the answer to my own question. I was not able to map the volume because I needed an additional package installed called libdevmapper that works hand and hand with DMSetup...

---

