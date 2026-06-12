---
title: "Firefox Update"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by Phade on 2007-02-10
I read the older post and the link that was given about firefox updating.  It said to move it to /opt.  I did. (mv ~/Desktop/firefox ~/opt).  Now I cannot make anything happen.  Before I moved the folder to /opt it was on my desktop (as you can tell from earlier in my post).  I tried this (~/Desktop/firefox$ sudo tar -zxvf updater.ini) and got this error message  would be 
(gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Error exit delayed from previous errors)

I am not sure where to go from here.  I am really trying to learn so I have read previous posts and googled it but have come up with nothing of use to me, or atleast nothing that I have made work.  Anyway the folder I extracted firefox to is still in /opt.  I just need to know how to install it so it will update my v1.5 firefox to v2.0 firefox.  Anyhelp would be appreciated.

Thanks !! :guitar:

---

### Post by Maestro23 on 2007-02-10
/opt is owned by root.  You will need to use "sudo" in front of your command.
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Firefox 2.0 is available in the Ubuntu repositories via synaptic also.

---

### Post by RomeReactor on 2007-02-10
Are you using Dapper or an earlier version of Ubuntu? Seeing as you joined the forums this month, one would think you're using Edgy.

---

### Post by Phade on 2007-02-10
THank you very much.  I have no clue what I did but it is installing the latest version of firefox.

---

### Post by Phade on 2007-02-10
Well damn ... It says I still have v1.5.0.9.  MY command line said this thought (The new Firefox version 2.0.0.1 has been installed successfully.)  Any thoughts?

---

### Post by Phade on 2007-02-10
> **RomeReactor said:**
> Are you using Dapper or an earlier version of Ubuntu? Seeing as you joined the forums this month, one would think you're using Edgy.

oops somehow I missed your post.  SOrry.  I am using 6.06

---

### Post by Phade on 2007-02-10
Now I feel like an idiot.  I thought all I had to do was to restart firefox ... but I had to restart my computer.  Excellent thanks for all the help !!

---

