---
title: "Webmail for Thunderbird flew out..."
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by gimpguy2000 on 2007-09-04
Just as I got my Thunderbird issue sorted, webmail will no longer work for my hotmail account.

Problems:

1. Installed Webmail
2. Installed Hotmail extension
<note, the above I have done in windows many times and even in Linux before and it worked fine>

3. I keep getting **cannot connect to local host or refused**. 
4. I am using my SBC yahoo accounts through pop just fine, those are working. 
5. I set the options for my ports over 1024 and they are running in Webmail, still won't connect. 
6. I am not using a firewall.
7. I am in user mode but that shouldn't affect it. 
8. Using Ubuntu Feisty. 
9. I am trying to connect to Live mail which there is an option for. 
10. I have read many other posts but none seem to fit my specific problem. 

Thanks,

Paul

---

### Post by saisho on 2007-09-04
Had some connection problem a couple of weeks ago and had to change my Hotmail Webmail extension settings to use the DEV(?) option.

---

### Post by gimpguy2000 on 2007-09-04
Hi, not sure on the Dev option, i'm still a little green to some things using Linux :(  I did more searching and most have solved the issue by setting higher ports, me, it won't work. 

TX

Paul

---

### Post by stchman on 2007-09-04
> **gimpguy2000 said:**
> Just as I got my Thunderbird issue sorted, webmail will no longer work for my hotmail account.

Problems:

1. Installed Webmail
2. Installed Hotmail extension
<note, the above I have done in windows many times and even in Linux before and it worked fine>

3. I keep getting **cannot connect to local host or refused**. 
4. I am using my SBC yahoo accounts through pop just fine, those are working. 
5. I set the options for my ports over 1024 and they are running in Webmail, still won't connect. 
6. I am not using a firewall.
7. I am in user mode but that shouldn't affect it. 
8. Using Ubuntu Feisty. 
9. I am trying to connect to Live mail which there is an option for. 
10. I have read many other posts but none seem to fit my specific problem. 

Thanks,

Paul

You do know that Hotmail allows POP access on paid accounts only.  There are a few that still have POP access on the free Hotmail accounts, but very few.

---

### Post by gimpguy2000 on 2007-09-04
> **stchman said:**
> You do know that Hotmail allows POP access on paid accounts only.  There are a few that still have POP access on the free Hotmail accounts, but very few.

Thanks for the reply. Well, I don't have paid but still access and was doing so through Windows prior so I knew that wasn't the issue. :( 
 I got it working but ONLY by setting my ports as 1024 and 1025. Any other combination won't work, why? I have no idea. :confused:
So typically as I do, I will list what I did so others may benefit... This does not include restarts, etc...that need to be done.

1. Create email account
2. pop>incoming>Localhost
3. Smtp >using default smtp>eg...sbc.yahoo.com
4. Install Web-mail and WM-Hotmail plugins
5. Webmail>Pop>1024   Smtp>1025
6. Web-mail Hotmail> new live
7. Account server settings>Set port to 1024
8. Give password, all set to go. 


These are what worked for me anyway. 

Cheers,

Paul

---

### Post by stchman on 2007-09-05
> **gimpguy2000 said:**
> Thanks for the reply. Well, I don't have paid but still access and was doing so through Windows prior so I knew that wasn't the issue. :( 
 I got it working but ONLY by setting my ports as 1024 and 1025. Any other combination won't work, why? I have no idea. :confused:
So typically as I do, I will list what I did so others may benefit... This does not include restarts, etc...that need to be done.

1. Create email account
2. pop>incoming>Localhost
3. Smtp >using default smtp>eg...sbc.yahoo.com
4. Install Web-mail and WM-Hotmail plugins
5. Webmail>Pop>1024   Smtp>1025
6. Web-mail Hotmail> new live
7. Account server settings>Set port to 1024
8. Give password, all set to go. 


These are what worked for me anyway. 

Cheers,

Paul

From everything I have read, Hotmail POP access is best done using Outlook Express.  It is no coincidence.

---

### Post by gimpguy2000 on 2007-09-08
> **stchman said:**
> From everything I have read, Hotmail POP access is best done using Outlook Express.  It is no coincidence.

True but if you don't use OE it's kind of moot. Of course i'm not sure you can use OE for this as I haven't read up on it lately. Prior with old Hotmail from MSN you could at one time access and import hotmail then MS decided to not allow this in OE anymore and has been so for a while. I can only assume since Hotmail is now strictly MS that they now MAY allow you to access and import yet again. Not sure if this is the case but just a guess. 

MS has locked out some 3rd party email handlers such as eprompter and such "not purposely" **so they say** but due to some server issues many 3rd party types could not access Windows live mail. 


I may be going back to the hog pit that is windows, I have been searching for another OS besides Ubuntu and was going back to Fedora but decided not to and to try some others. I am frustrated with Ubuntu and tired of doing more repair work for things that are** supposed** to work but don't.  I can't even share files properly on here, went through 7 hours of fixes and such and still nothing. So, I may be finding out more about what OE can or can't do soon. :( 


Paul

---

