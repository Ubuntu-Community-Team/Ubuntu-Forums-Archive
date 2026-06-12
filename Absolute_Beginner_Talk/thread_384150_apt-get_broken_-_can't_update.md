---
title: "apt-get broken - can't update"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by sandydesu on 2007-03-14
Hey,

I am running Kubuntu edgy-eft and apt-get has broken. It is refusing to update and whenever I open adept, instead of listing all of packages available to install, it only lists the ones which are already installed.

When I type in "sudo apt-get update" in bash I get the following:

Err [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) edgy-updates Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) edgy-updates/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) edgy-updates/restricted Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) edgy Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) edgy/universe Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) edgy/multiverse Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) edgy-backports Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) edgy-backports/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) edgy-backports/restricted Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) edgy-backports/universe Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) edgy-backports/multiverse Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

I have not installed any new packages recently or upgraded anything.  My other Internet services are fine and it is not my firewall blocking anything. Anyone have any ideas? The only "untoward" thing that I did before this happened was to run adept offline at work, look for some programs I wanted to install, selected them and put my laptop into hibernate. When I got home, I re-started the computer online from hibernation and then this happened.  Looking forward to any ideas anyone might have. Thanks in advance.

---

### Post by chuckyp on 2007-03-14
Are you in japan?

---

### Post by Kateikyoushi on 2007-03-14
Can you open those urls in the browser ? The adresses work for me.

---

### Post by EdThaSlayer on 2007-03-14
If that repo fails you can try making another source from scratch.
Visit 

[Full source]("http://www.debianadmin.com/ubuntu-edgy-eft-complete-sourceslist-repository-list-file.html")

or 

[URL="http://3v1n0.tuxfamily.org/blog/lista-repository-sourceslist-ottimizzata-per-ubuntu-kubuntu-linux/"]
Travinos source list[/URL]

Those two above are the sources for Edgy Eft.

---

### Post by sandydesu on 2007-03-14
Thanks for the quick responses. In answer to the responses thus far:

1) Yes, I am in Japan.

2) Those urls work fine in my browser.

3) I will try the  new repo lists, thanks.

The thing is, I think the repo lists are fine, it is my computer that is refusing the connection and I don't know why.  The firewall is not getting in the way and all other internet services work perfectly. Still trying though...

---

### Post by Kateikyoushi on 2007-03-14
You could try to switch to other servers, or change the http to ftp.
Don't know why does it happen but this is the first time I heard about the japanese server, though only us and main servers are effected.

---

### Post by sandydesu on 2007-03-14
Dear Kateikyoushi (nice name home teacher, but why?)

You are obviously in Japan too, is this happening on your box as well?

Thanks for your help,

Sandydesu (dumb I know)

---

### Post by sandydesu on 2007-03-14
Dear Kateikyoushi,

Thanks a lot! I changed http to ftp and now everything is working fine. You have been realy helpful and I really appreciate it a lot.

---

### Post by Kateikyoushi on 2007-03-14
Why Kateikyoushi ? Well I tried to create a second mail for myself a long time ago and I was running out of childhood heroes and as inspiring the uni lab is most likely few thousand people tried  the same words as username before me. Then I noticed already I am already late for my part time job, so just tried that and worked, in the end it stuck on me. Talking about dumb.

I did not experience this with apt yet and I think you are the first from Japan, so far I thought it happens only on the us and main servers.
Glad to know it worked.

---

