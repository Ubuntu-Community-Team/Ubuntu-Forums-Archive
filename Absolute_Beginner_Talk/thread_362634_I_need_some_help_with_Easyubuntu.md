---
title: "I need some help with Easyubuntu"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by NET WT on 2007-02-15
Hello,

I installed Ubuntu on my computer today. The install was easy and fast, I like so far. I am having trouble with Easyubuntu though. Earlier I tried to install codec with terminal, I tried to follow the instructions here: 

[http://www.ubuntuforums.org/showthread.php?t=182902&highlight=How+do+I+get+mp3+to+play%3F]("http://www.ubuntuforums.org/showthread.php?t=182902&highlight=How+do+I+get+mp3+to+play%3F")

I copy and paste, but I was not able to get it to work. Then I accidentally clicked remove and removed something in Software Properties. Then I installed Easyubuntu, it doesn't work. 

I need help to undo what I did, so this Easyubuntu will work. So I can listen to mp3, and watch movies. 

Thank you.

---

### Post by Sklasko on 2007-02-15
Well, the reason that the guide you tried to use didn't work is because you probably haven't enabled all other repo's in your sources.list.

More about that [Here]("https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto").

As for what you accidently removed, you may want to check with the logs for synaptic to figure out just what it was you removed. I don't know where synaptic keeps it's log, I'm not well versed on logs stored in /var but hopefully someone else can weigh in and help you figure out the issue.

---

### Post by hmLyons on 2007-02-15
I'm not exactly following what you have done. What 'Software Properties' are you talking about? Do you mean in Synaptic?

Try Automatix. It does pretty much the same thing as EasyUbuntu. Here are [the instructions]("http://www.getautomatix.com/wiki/index.php?title=Installation#Installing_Automatix2_with_Apt").

---

### Post by NET WT on 2007-02-15
After I tried to use the terminal. I went to "System" > "Administration" > "Software Properties" and tried to add the Universe and Multiverse Repositories. Then I accidentally clicked remove, and removed something called "Ubuntu 6.06 LTS (source)"

---

### Post by hmLyons on 2007-02-16
Other than playing MP3s is there something else in your system that is now broken?

I'm running a newer version of Ubuntu so I can't confirm it but I think that the "Ubuntu 6.06 LTS (source)" you are talking about is unnessisary, since all it does is install the [source code]("http://en.wikipedia.org/wiki/Source_code#Purposes") with the programs. If that is the case you will see something in the same list that is the regular non-source version named like "Ubuntu 6.06 LTS".

To make sure that you have all the nessisary repositories you can follow [these instructions]("http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories").

Now if your system is okay, then we can focus on getting your MP3 playback working. When you say that you followed those instructions to install EasyUbuntu but it didn't work... can you elaborate on this? What didn't work? Did you see an error or is it just that MP3 playback is just not working? Does regular sound work but not MP3s?

---

### Post by NET WT on 2007-02-17
I installed Automatix. I am now able to listen to mp3 and watch wmv. thanks

---

