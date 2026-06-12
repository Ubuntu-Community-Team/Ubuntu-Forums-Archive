---
title: "java"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by SMS on 2007-03-16
hey guys 
whenever install something i get this in the details box (see pic)

cheers sms

---

### Post by irwa82 on 2007-03-17
Hi,

The message says you have to download the 2 .zip files and put them in /tmp with permissions of root.root

Download the to zip files into a directory then do the following.

sudo cp *.zip /tmp
sudo chown root.root /tmp/*.zip

Then try reinstalling the package.

---

### Post by SMS on 2007-03-17
where can i get the zips from when i go to sun-java website they are no zips they are some other self-extracting files and when i copied them into /tmp the thingy didnt recognise them
thanks for the reply btw

---

### Post by SMS on 2007-03-17
thanks for the reply
but where can i get the zips from when i go to sun-java website they are no zips they are some other self-extracting files and when i copied them into /tmp the thingy didnt recognise them

---

### Post by irwa82 on 2007-03-17
Hi,

I had a quick look on the java site for you and I guess the navigation could be better but I did find the section for the two zip files.

Go to the link below then on that page towards the bottom you will see the 'Java SE 6 Documentation' click the download button in that section and the two zip files are there.

[http://java.sun.com/javase/downloads/index.jsp](http://java.sun.com/javase/downloads/index.jsp)

---

### Post by SMS on 2007-03-18
thanks mate u rule

---

