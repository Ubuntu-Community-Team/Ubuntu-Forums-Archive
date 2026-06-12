---
title: "Installing downloaded files with .tar.gz extensions"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by lylesantos on 2007-07-04
Hi, I am new to linux and have been using Ubuntu for a month now. I recently downloaded and installed Audacity via automatix.

However, the install didnt include LAME encoders due to patent issues so I had to downloadit separately.

My problem lies with installation. Just like any other app that I download directly from the internet, I do not know how to install files with **.tar.gz** extensions.

Any step-by-step guide would greatly be appreciated.

BTW, I "googled" for some DIY guides but I can't seem to follow it. So, please be kind enough to post a guide specific to installing a file called **lame-3.97.tar.gz** which I downloaded to my Desktop.

Thanks!

---

### Post by Brucevdk on 2007-07-04
In most cases you shouldn't have to download files from websites as you probably were used to. Try to search for the package you want to install in Synaptic, or browse the categories for software you might like. See:

[LIST]
[*][How to install ANYTHING in Ubuntu!]("http://www.monkeyblog.org/ubuntu/installing/")
[*][Phsychocats.net: Installing software]("http://www.psychocats.net/ubuntu/installingsoftware")
[/LIST]

For example LAME can be installed by installing liblame0 via Synaptic or using the following command in a terminal:
```

sudo apt-get install liblame0

```

What I also don't get is why would you use Automatix for installing Audacity? It's in the repositories and you could just install it via Synaptic.

---

### Post by lylesantos on 2007-07-04
i used automatix because i didnt know better.. im a linux newbie. 

is synaptic add/remove in ubuntu 7.04? im really new to this. i mentioned that i googled some guides (the same ones that you listed in your reply) and that i wasnt able to follow the instructions..maybe due to being a windows user since windows 3.1

anyway, the code you gave worked like a charm. thanks!

---

### Post by Bluecircle on 2007-07-04
Synaptic is under System -> Administration -> Synaptic Package Manager. It's like Add/Remove except it shows everything in the repositories that can be installed.

---

