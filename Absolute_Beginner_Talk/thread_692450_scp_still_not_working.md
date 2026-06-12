---
title: "scp still not working"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by Red-Shield on 2008-02-09
red-shield@FederalReserve:~$ scp -r /home/serial-killer/baby_pics red-shield@192.168.1.100:/home/red-shield/Desktop
red-shield@192.168.1.100's password: 
/home/serial-killer/baby_pics: No such file or directory
red-shield@FederalReserve:~$ 



serial-killer@AMD64:~$ pwd
/home/serial-killer
serial-killer@AMD64:~$ cd baby_pics
serial-killer@AMD64:~/baby_pics$ ls
S5030957.JPG  S5030960.JPG  S5030963.jpg  S5030966.JPG
S5030958.AVI  S5030961.JPG  S5030964.JPG  S5030967.JPG
S5030959.AVI  S5030962.JPG  S5030965.AVI  S5030968.AVI
serial-killer@AMD64:~/baby_pics$ pwd
/home/serial-killer/baby_pics
serial-killer@AMD64:~/baby_pics$ 


can someone tell me what is wrong with this string trying to scp a directory between boxes. the file is there and all is spelled right. above is the print from serial-killer which has the directory and above that is the string i used to retreve the directory any help would be great. thanks thanks thanks

---

### Post by Dr Small on 2008-02-09
SCP can be confusing, so don't feel bad.
Try this though:
```
scp -r /home/serial-killer/baby_pics red-shield@192.168.1.100: Desktop/
```

---

### Post by LookTJ on 2008-02-09
See if creating the directory then scp'ing the directory works?

---

### Post by Red-Shield on 2008-02-09
that string copys my whole home folder from red-shield i want to copy the baby_pics folde rthe whole thing from serial-killer to red shield Desktop. sorry used to sftp

---

### Post by p_quarles on 2008-02-09
From the look of it, you've got the remote and local hosts backwards. In your first post, the baby_pics directory appears to be on a host called AMD64, whereas the scp command is looking for that directory locally on the host called FederalReserve. 

I may be overlooking something obvious here, but that's what popped out in my mind.

---

### Post by Red-Shield on 2008-02-09
serial-killer@AMD64:~$ scp -r red-shield@192.168.1.100:/home/red-shield/Music* ~/Desktop

this is the string i needed wow i cant belive how many combos i tried to get here but now that it is done thank you all for your help.

---

### Post by Red-Shield on 2008-02-14
> **p_quarles said:**
> From the look of it, you've got the remote and local hosts backwards. In your first post, the baby_pics directory appears to be on a host called AMD64, whereas the scp command is looking for that directory locally on the host called FederalReserve. 

I may be overlooking something obvious here, but that's what popped out in my mind.

thanks for your help of all the people out there trying to give advise on the subject it was you that helped me so thanks

---

