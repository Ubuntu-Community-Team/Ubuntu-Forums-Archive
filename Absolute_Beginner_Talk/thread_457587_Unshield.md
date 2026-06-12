---
title: "Unshield ?"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by tgbrowning on 2007-05-28
From that walk through to install ndiswrapper for WUSB54GS (linksys USB wireless),  there's the following:

>>You then need to get a hold of unshield. To do this, goto System  >>Administration -> Software Properties and check every box you >>see there. Click the "close" button, and let it "reload" the >>packages. Then 
>>run this command:
>>Code:
>>sudo apt-get install unshield
>>Then run this command on the two cab files in the unzipped EXE:

I have a 6.06 installation CD and unshield appears to be completely absent from it.  So, I came on line and found the source code and a slew of other things, but I'm unsure what I should be downloading to my XP machine to transfer to my Ubuntu machine via a thumb drive.

Could someone kind of explain where and how things are found in the Ubuntu universe? I'm a bit in the dark here.

Browning>>>

---

### Post by starcraft.man on 2007-05-28
> **tgbrowning said:**
> From that walk through to install ndiswrapper for WUSB54GS (linksys USB wireless),  there's the following:

>>You then need to get a hold of unshield. To do this, goto System  >>Administration -> Software Properties and check every box you >>see there. Click the "close" button, and let it "reload" the >>packages. Then 
>>run this command:
>>Code:
>>sudo apt-get install unshield
>>Then run this command on the two cab files in the unzipped EXE:

I have a 6.06 installation CD and unshield appears to be completely absent from it.  So, I came on line and found the source code and a slew of other things, but I'm unsure what I should be downloading to my XP machine to transfer to my Ubuntu machine via a thumb drive.

Could someone kind of explain where and how things are found in the Ubuntu universe? I'm a bit in the dark here.

Browning>>>

[Here]("http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_add_extra_repositories") you go, quick guide to enabling all the extra repos for 6.06. I'm sure once ya enable em all and update it'll be ok, then just open the terminal and put in the command you put in your question:

```
sudo aptitude install unshield
```

that should do it :).

---

### Post by tgbrowning on 2007-05-28
I'll give it a shot and let you know.  Thanks!

Browning>>>

---

