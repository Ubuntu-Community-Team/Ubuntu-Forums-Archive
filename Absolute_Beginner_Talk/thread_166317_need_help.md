---
title: "need help"
date: 2006-04-26
forum: Absolute Beginner Talk
---

### Post by vishrut on 2006-04-26
i am nu 2 ubuntu n linux rather.i'm not able 2 login as root user n whenever i start ubuntu i get this message "Could not look up internet address by ubuntu.This will prevent GNOME from working correctly.It may be possilbe to correct the probloem by adding ubuntu to the file /etc/hosts " i've tried everythin but in vain n 1 more thing i dont have net connec on my comp.could this be the problem.please help.

---

### Post by Sef on 2006-04-26
1) Try this first:  System > Administration > Networking

2) If it doesn't work, what type of connection do you have?

3) By default, Root is locked down in Ubuntu for a number of reasons.  Click on the link to find out why.

[https://wiki.ubuntu.com/RootSudo?highlight=%28RootSudo%29]("https://wiki.ubuntu.com/RootSudo?highlight=%28RootSudo%29")

---

### Post by mjm115 on 2006-04-26
Well, for starters you can not log on as root.  It's a security issue.  You can find more info about that [here]("https://wiki.ubuntu.com/RootSudo").

Because you don't have a connection to the net, this is why you're receiving these connection errors.  Once you get a connection to the net, you should stop receiving them.

---

### Post by Haegin on 2006-04-26
Ok, firstly welcome to the forums. Just a bit of advice before I start on the problem. 
Give your posts useful titles. "Need help" is not very useful and means that I dont know what you need help with. "Internet not working" is a far better title as that describes the problem.
Also spellcheck your posts before you submit them. There are many users on this forum who are do not speak native english and people will find it alot harder to help you if they dont understand what you are saying. On top of that some people just wont answer questions if the author hasn't bothered making it easy to read. There are many questions to answer so why should they spend time deciphering your question when they could be answering someone elses?

Now, on to your problems.
You **dont** want to **ever** login as root. It carries all kinds of security risks and has no benefits. Instead you login as the user you created during the install and when you try to run a program that needs root privilages you will be asked for the root password (which should be the same as your own).

Now to sort out your internet. I will need more information before I know for sure how to fix it.
How do you connect to the internet? Do you use dial-up? ADSL? A home network? What do you mean by "i dont have net connec on my comp"? Do you mean you dont have internet access or that you are not on the network?

---

