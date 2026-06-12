---
title: "Ran Thunderbird install script &quot;sudo ./firefox&quot;..."
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by jpupecki on 2007-03-20
Hello All,

  Ubuntu is running great! My nVidia is work awesome, thanks to Envy! Even got my Lexmark X125 running!

  But I made an error when I installed Mozilla Thunderbird, I ran the install script with the command "$sudo ./thunderbird", it installed, but I found to run it I had to launch it with the command "$sudo thunderbird". I am sure this is a permission issue. Worst part is it hosed my Firefox install also. Even though I had already installed firefox, and it was running fine, it now also requires sudo prefixed on the command to launch it. 

  I removed both applications and reinstalled, including just about everything that made sense in synaptic under a search on keyword "mozilla". NO JOY! Well it did resolve the issue with thunderbird, but NOT FIREFOX!

HELP!!!!

Thanks, Joe
:confused:

---

### Post by twikletoes on 2007-03-20
What version of Ubuntu are you using?
If you are using 6.10 i suggest you just use you sudo apt-get install mozilla-thunderbird firefox
 They should both install just fine and be able to use them

---

### Post by jpupecki on 2007-03-21
Twikletoes,

   Thanks for the response, it didn't work however...  :( 

  I did "apt-get install firefox", and of course apt-get indicated that firefox was already present on the system...

  So I did "apt-get install firefox --reinstall", which apt-get liked better, did the re-install, but I have the same issue. 

  I still have to type "sudo firefox" to start firefox successfully.

  If I try to launch firefox without he "sudo" I see a task bar button, says "starting Firefox Web Browser", which dies after about 5-7 seconds...

Thanks, Joe

---

### Post by Bachstelze on 2007-03-21
```
ls -l ~/.mozilla
```

What does that give you ?

---

### Post by twikletoes on 2007-03-21
why don't you try sudo apt-get autoremove firefox

Then you should be able to sudo apt-get install firefox.

---

### Post by jpupecki on 2007-03-21
HymnToLife,

  You ROCK!, I should have guessed that! After a remove and reinstall, I should have known the personal file data was what got left behind (it's left behind to preserve personal settings), therefore the permissions didn't get corrected when I reinstalled!

  So what I did was "sudo chown *myusername* ~/.mozilla", then "sudo chgrp *myusername* ~/.mozilla", the checked the contents of the ~/.mozilla directory to be sure all files within had the correct owner and groups and it's all set! Thanks Hymn!!! :guitar:  _YOU ROCK!!_

  Hey, you're also kinda cute!

Twikletoes, see above for why your solution didn't/wouldn't have worked... THanks for the help though!

Thanks to you Hymn! and Thanks to all who read this and thought about it!
Joe

---

