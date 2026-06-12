---
title: "Open Allure DS"
date: 2010-06-14
forum: Assistive Technology &amp; Accessibility
---

### Post by shaolin77 on 2010-06-14
Hello Everyone, 
   Wondering if you any of you are familiar with Open Allure DS..I've starting trying to get this working on Ubuntu 10.04 ...but have run into a road block.   

Open Allure is an open source python based project aimed to develop voice and gesture recognition.  

The one road block I've run into is the voice components...per some of the info I've read so far this project uses dragonfly.   Open Allure DS is meant to be used by Windows, Mac and Linux and I'm not sure as to how to get the voice part going for Ubuntu.   Reading a bit of the documentation you can use eSpeak..but not sure how to get it going with eSpeak...any help would be greatly appreciated.

Thanks!

---

### Post by Thorney on 2010-06-23
Hi,
I've got the speech synthesis going on Ubuntu 10.04 you need to install espeak and python-espeak via synaptic. Then in the open-allure directory open the *openallure.cfg* file - at this stage it doesn't automatiacally know you have espeak so you have to set the useEspeak variable to 1.

I'd be interested to hear how you get on! And if you want to submit patches that would be great!

---

