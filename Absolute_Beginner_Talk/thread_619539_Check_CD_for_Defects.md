---
title: "Check CD for Defects"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by malbo on 2007-11-21
Hi,
a question on the "Check CD for Defects" (choice at the CD menu).
I assume that a md5sum check is performed inside this program "Check CD for Defects"? could you confirm that ?

---

### Post by Pumalite on 2007-11-21
Integrity means just that. You have to do md5sum on iso before burning.

---

### Post by malbo on 2007-11-23
Hello Pumalite,
thank you for your answer but I am not sure to understand :my question is not on the md5sum on iso before burning. My question is : inside the program "Check CD for Defects", is there a check of md5sum ( Hidden for the user) yes or not ?

---

### Post by jaybombalous on 2007-11-23
when u run Check CD for defects on the live cd u are checking every file on the cd against a md5sum. The md5sum's are located in a txt file on the cd.

---

### Post by Pumalite on 2007-11-23
That md5sum is not the same as the iso. That is merely what the CD collects at the start of the burn, so it does not truly represent the md5sum of the iso, merely what the burner found when it started burning, You have to start with a good iso first.

---

### Post by malbo on 2007-11-24
Thanks for your help, jaybombalous and Pumalite.
I don't confirm your opinion Pumalite : I made md5sum on the liveCD and I find the same md5sum "signature" as the md5sum of the iso. Therefore, I think that md5sum on the liveCD is possible but probably unnecessary because the program "Check CD for Defects" can realize the same operation automatically.

---

### Post by Pumalite on 2007-11-24
That's because you started with a good iso. Meaning; that md5sum has to coincide too with the one provided by the site where you downloaded from.

---

