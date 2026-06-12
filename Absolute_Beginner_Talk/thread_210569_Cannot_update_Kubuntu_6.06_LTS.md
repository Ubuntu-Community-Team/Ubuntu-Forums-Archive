---
title: "Cannot update Kubuntu 6.06 LTS"
date: 2006-07-07
forum: Absolute Beginner Talk
---

### Post by fer5437 on 2006-07-07
I just get a free CD from Kubuntu org and had install it on my pc. Everything is fine but I just cant update and upgrade it.

> Password:
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper Release.gpg
  Could not connect to au.archive.ubuntu.com:80 (130.95.3.26). - connect (111 Connection refused)
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates Release.gpg
  Could not connect to au.archive.ubuntu.com:80 (130.95.3.26). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
  Could not connect to security.ubuntu.com:80 (82.211.81.138). - connect (111 Connection refused)
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg](http://au.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg)  Could not connect to au.archive.ubuntu.com:80 (130.95.3.26). - connect (111 Connection refused)
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg](http://au.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg)  Could not connect to au.archive.ubuntu.com:80 (130.95.3.26). - connect (111 Connection refused)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg)  Could not connect to security.ubuntu.com:80 (82.211.81.138). - connect (111 Connection refused)
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.
jsleong@g-cg-jsleong:~$ sudo apt-get update
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
  Could not connect to security.ubuntu.com:80 (82.211.81.138). - connect (111 Connection refused)
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper Release.gpg
  Could not connect to au.archive.ubuntu.com:80 (130.95.3.26). - connect (111 Connection refused)
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates Release.gpg
  Could not connect to au.archive.ubuntu.com:80 (130.95.3.26). - connect (111 Connection refused)
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg](http://au.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg)  Could not connect to au.archive.ubuntu.com:80 (130.95.3.26). - connect (111 Connection refused)
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg](http://au.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg)  Could not connect to au.archive.ubuntu.com:80 (130.95.3.26). - connect (111 Connection refused)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg)  Could not connect to security.ubuntu.com:80 (82.211.81.138). - connect (111 Connection refused)
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.


Do you guy have any idea of this?? Thank you in advanced

---

### Post by Yes_It's_Me on 2006-07-07
seems like your internet is not connected go to network settings  and see

---

### Post by fer5437 on 2006-07-08
Yes my internet connection is connected because I can use Konqueror   to go online. Is there any other issues there because of this???

---

### Post by lazyrussian on 2006-07-08
I am having the same exact problem too.
I'm also trying to install crossover office and im' having an X.org Display problem???

---

### Post by FredB on 2006-07-08
> **fer5437 said:**
> I just get a free CD from Kubuntu org and had install it on my pc. Everything is fine but I just cant update and upgrade it.

Do you guy have any idea of this?? Thank you in advanced

Seems like au. mirror is down.

Try this.

[LIST=1]
[*]Open a Konsole
[*]type in it sudo kedit /etc/apt/sources.list
[*]use the search / replace function by replacing "au." by "" (without quotes, of course)
[*]save your file
[*]try again updating.[/LIST]Hope it helped ;)

---

### Post by MaximB on 2006-07-08
I have the same problem with the last updates in ubuntu
what shell I do ?
the mirrors are broken

---

### Post by fer5437 on 2006-07-10
After few day of trying, at last I found the solution for my problem. Here I connect to internet through proxy. So what I do is type export http_proxy=http:123.3.2.123:8080 in terminal. And everything look fine after that. 123.3.2.123 is the proxy setting.

---

