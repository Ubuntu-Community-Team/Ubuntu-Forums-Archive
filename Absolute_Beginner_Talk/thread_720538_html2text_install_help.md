---
title: "html2text install help"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by cloudyscreen on 2008-03-10
Hi,

I cant install html2text.

I've tried sudo apt-get install /home/username/desktop/html2text
but get error message saying that the file is not found

I've tried sudo dpkg -i......but get the same message.

I cant get debhelper installed until I've install html2text, but nothing seems to have worked so far.

I haven't got an internet connection but I've download html2text and put it on my desktop.

Someone please tell me where I'm going wrong.

thanks 

cloudy

---

### Post by kwacka on 2008-03-10
If you really want to install the file you've downloaded, open terminal type:```
 cd Desktop
sudo dpkg --install html2text
```

Alternatively, use Synaptic Package manager to install the versions from the repository.

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by FuturePilot on 2008-03-10
Try this
```
sudo apt-get install html2text
```

---

