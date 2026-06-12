---
title: "file name contains spaces"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by iulian on 2007-02-03
Hello,

Like a complete newbie I have a silly question: is it possible to download a file from a ftp if filename contains spaces? I use wget to do that but is not working because of the spaces from filename.

Thanks!

---

### Post by taurus on 2007-02-03
Try

```
wget -c "file name"
```

---

### Post by iulian on 2007-02-03
I try that and it seems I have a problem. I run this: wget -b --output-file=/home/iulian/downloads/log.txt --tries=0 --quota=800m --limit-rate=5k --ftp-user=x --ftp-password=x [ftp://ftp.server.com/Download/!!!%20in%20folder/filetodownload.avi](ftp://ftp.server.com/Download/!!!%20in%20folder/filetodownload.avi)

If I look in log.txt I see that the path to file to download is incorrect. An that is because near Download/ is inserted something like ls or a command runed by me before. Why is this happening?

---

### Post by finer recliner on 2007-02-03
if there are spaces in a path, either wrap the path in quotes, or place a \ (forward slash) in front of any spaces that appear in the path. the forward slash is an escape character, meaning it will not treat the space as it normally would (a break point between arguments) but as a character in the the same argument currently being processed.

---

### Post by Spr0k3t on 2007-02-03
Try escaping the spaces by putting a backslash (\) before the space.

Like this
wget -c [ftp://ftp.server.com/Download/!!!\](ftp://ftp.server.com/Download/!!!\) in\ folder/filetodownload.avi

If this file is there, you shouldn't have any problems.

---

### Post by iulian on 2007-02-03
Feedback: -bash: !\: event not found.

---

### Post by Spr0k3t on 2007-02-03
Escape your bangs

wget -c [ftp://ftp.server.com/Download/\!\!\!\](ftp://ftp.server.com/Download/\!\!\!\) in\ folder/filetodownload.avi

That should force it through.

---

### Post by bodhi.zazen on 2007-02-03
Do notuse a !

Say the name of the File is **File Name**

Then use **File\ Name**

---

### Post by iulian on 2007-02-03
It works with "\!". Thanks guys!

bodhi.zazen, Directory name contains !!!. I can't rename it because I don't have permission.

---

