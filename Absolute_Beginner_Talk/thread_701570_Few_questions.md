---
title: "Few questions"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by onthefence on 2008-02-19
1. Does anyone have a problem with emails in Evolution/Thunderbird where there is a "nested" email, such as in a forwarded email, where the "nested" portion gets embedded as an attachment called "winmail.dat". I have a dual boot with Windows and have been using Outlook and in that situation, you can open the message attachment, however, when I switched to Evolution/Thunderbird I started seeing this "winmail.dat" attachment a lot more and not getting the forwarded message.
Any solutions?

2. Is there a difference between "logging in as root" and using "sudo" in your commands? How does one "log in as root"? 

3. Does anyone have trouble playing streaming windows media, such as .asx? Are there any known solutions for this? I downloaded a streaming codec but still no luck?

4. Is there a program that will automatically alternate desktop images from a user-specified folder of pictures? 

5. Anyone suggest a good program to clone DVDs(unencrypted), burn data DVDs, CDs, etc.?

Thanks

---

### Post by billgoldberg on 2008-02-19
> **onthefence said:**
> 1. Does anyone have a problem with emails in Evolution/Thunderbird where there is a "nested" email, such as in a forwarded email, where the "nested" portion gets embedded as an attachment called "winmail.dat". I have a dual boot with Windows and have been using Outlook and in that situation, you can open the message attachment, however, when I switched to Evolution/Thunderbird I started seeing this "winmail.dat" attachment a lot more and not getting the forwarded message.
Any solutions?

2. Is there a difference between "logging in as root" and using "sudo" in your commands? How does one "log in as root"? 

3. Does anyone have trouble playing streaming windows media, such as .asx? Are there any known solutions for this? I downloaded a streaming codec but still no luck?

4. Is there a program that will automatically alternate desktop images from a user-specified folder of pictures? 

5. Anyone suggest a good program to clone DVDs(unencrypted), burn data DVDs, CDs, etc.?

Thanks

1. Don't use email clients

2. Yes. Sudo makes you root for a little time (think it's 5 minutes). Loggin in as root makes you root all the time. This is not good for anyone. Ubuntu disables the root account by default I guess. You can still use 'sudo su' or open the file manager as root -> "sudo nautilus".

3. windows media stream good for me. I use packages form the medibuntu repo/

4. [http://www.getdeb.net/app.php?name=Wallpapoz](http://www.getdeb.net/app.php?name=Wallpapoz)

5. ripping -> k9copy | burning k3b

---

### Post by Het Irv on 2008-02-19
1. Outlook is coded so that some e-mails can only be opened in Outlook. Stupid Microsoft.
2. Sudo elevates the current user to root status, In Ubuntu you cannot login as root. (Security Reasons)

I don't know about the other three questions.

---

### Post by dje on 2008-02-19
hi

1. don't know sorry
2. logging in as root is disabled by default and it is advised that you do not enable it, sudo grants you root privileges for a command
3. don't know sorry
4. have a look [here]("http://ubuntuforums.org/showthread.php?p=4296272")
5. You could try dvd::rip, gnomebaker, k3b or brasero

hope that helps you on 2, 4 and 5

dje

---

### Post by Tatty on 2008-02-19
For 3.  Have you gone through this wiki page? [https://help.ubuntu.com/community/Multimedia]("https://help.ubuntu.com/community/Multimedia")

---

### Post by onthefence on 2008-02-20
Thank you all for your replys, although I have not had the time to try everything out yet. 
They all seem very helpful, except for billgoldberg's suggestion to stop using email clients. Not sure why anyone would not use them if they understood the benefits.

Stupid Microsoft! Just wanted to second that. Very interesting but not surprising. I would love to read more about that Het Irv if you know where I can find more info on that.

5 minutes as root seems long enough to follow a procedure, makes sense for them to disable it on ubuntu since it is sort of designed to be newbie friendly.

Again, thanks

---

### Post by mivo on 2008-02-20
As for the mail problem, please see [this link]("https://answers.launchpad.net/ubuntu/+source/evolution/+question/22051"). It offers solutions for both Evolution and Thunderbird. :)

---

