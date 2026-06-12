---
title: "off-line repository"
date: 2006-08-21
forum: Absolute Beginner Talk
---

### Post by Rainmaker_mail on 2006-08-21
Dear All,
I am still having problem with my apt-get update so i am thinking of create an off-line repository.
I've downloaded the deb file from [http://archive.ubuntu.com/ubuntu/dists/dapper](http://archive.ubuntu.com/ubuntu/dists/dapper) and moved it to /var/cache/apt/archives.
I then tried to apt-get install packages (for the ispconfig cookbook) but still have errors.
Next, i tried to create a packages file for the *.deb that i downloaded but i couldn't find dpkg-scanpackages: command not found.

Can anyone tell me 
1. if i need to download the dpkg-scanpackages ? which package?
2. is there an iso image of the repositories which we can download? It will save so much hassle and frustration if we can just download an iso to burn and use it to install our packages cos right now i am stuck.

Rgds,
RM

---

### Post by Kobalt on 2006-08-21
Hi,
Why don't you tell us what kind of problem do you have with Synaptic, because what you're asking, creating an iso of the repositories, is quite odd I think...

---

### Post by Rainmaker_mail on 2006-08-21
Hi,
Thank you for your reply.

My system is a Sun Ultra10 running ubuntu 6.06LTS Server version without desktop gui. I am trying to use apt-get update to update my applications but has errors -
"failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-sparc/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-sparc/Packages.gz)  Error reading from server. Remote end closed connection"

My sources.list is the basic "deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted"

I couldn't resolve my error and thinking it might be my internet connection - i am trying to create an offline repository. However, even after downloading the deb to /var/cache/apt/archives - i still can't install my packages. And i do not have dpkg-scanpackages command.

so Question # 1, where do i get the dpkg-scanpackages command?
Question # 2, the error from "apt-get update" command - is it due to internet connection slow?

Rgds,
RM

---

### Post by uberg on 2006-08-22
Did you change your repository list in Synaptic to point to your offline repository?  The connections can be slow at times.  i have had this problem too and have just tried to do the updates/intalls at a later time.

---

