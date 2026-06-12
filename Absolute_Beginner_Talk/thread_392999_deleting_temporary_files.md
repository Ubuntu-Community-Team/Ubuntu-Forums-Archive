---
title: "deleting temporary files"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by hardikorama on 2007-03-25
i have alloted just 4 gb of storage for my ubuntu partition. as a result, there is only about 800 mb of free space in the partition (after i fully updated it and installed a few softwares and themes). now i have a feeling that ubuntu uses a certain amount of space during installation which can be freed later. would anyone be so gracious as to share a code for retriving that space? any other ideas for freeing space are welcome too.

---

### Post by hardikorama on 2007-03-25
bump

---

### Post by Sef on 2007-03-25
Read [Removing Junk Files]("http://doc.gwos.org/index.php/RemoveJunkFiles").  (Note: The site seems to be down now.)

---

### Post by hardikorama on 2007-03-25
yup. that site is indeed down. do you, by chance, have any other link? and if the code is easy to understand, would you mind sharing it? thanks.

---

### Post by Malta paul on 2007-03-25
You could try in the terminal >sudo apt-get autoremove.
Also temporary files are held in a folder in your root , its called TMP, But if you delete these  I am not sure if this will screw your system? :confused:  Hope this may help:)

---

### Post by hardikorama on 2007-03-25
thanks. i kinda tried that earlier (got it from automatix). it does work but what i am looking for is a tool for removing all non-required files (not only installation files). do you know any? thanks again for replying.

---

### Post by Sef on 2007-03-25
That site has a number of commands to clean your system.  I just don't know them offhand.

---

### Post by dejitarob on 2007-03-25
Google cached page of that site: [http://209.85.165.104/search?q=cache:8h5OtnLSKj8J:doc.gwos.org/index.php/RemoveJunkFiles+http://doc.gwos.org/index.php/RemoveJunkFiles&hl=en&strip=1](http://209.85.165.104/search?q=cache:8h5OtnLSKj8J:doc.gwos.org/index.php/RemoveJunkFiles+http://doc.gwos.org/index.php/RemoveJunkFiles&hl=en&strip=1)

---

### Post by hardikorama on 2007-03-25
thanks. it worked.

---

