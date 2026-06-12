---
title: "Can I remove the password"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by lodbergs on 2006-09-10
Hi all

I've tried the search function but without luck - therefor this tread...

Is it possible to remove the password on my system. I've only got 1 user on it but isn't possible that I can give that user admin rights without typing in a password?

Regards, Søren

---

### Post by Abstract on 2006-09-10
If you mean at login you can go to:

System -> Administration -> Login -> Security -> Enable Automatic Login

If you mean prompts asking you for your password and the sudo commands this is possible and it is called running as root. This is **highly** discouraged as it makes your system as unsecure as a windows system with no antivirus. Possibly more unsecure.

---

### Post by arkangel on 2006-09-10
you can enable automatic login  in administration>>system>>login window
and then in the security tab, mark automtic login for your user or as you want for root. 

why do you want to do this ? I dont see the point of removing the password for administration tasks
it is simply too dangerous  you can be on top of your root system and erase a n important file  that you shouldnt  erase, just to mention one example. this is why linux is secure , anyway i was trying to enter an empty password,  and i couldnt , so i think it is not possible  , and i am happy it is not.

there is a distro Linspire or something, i read  that by default  does what  you want  (not sure ) but this feature is one of its major drawbacks

Edit:
doing  so as abstract says:  it may happens this 
[http://ubuntuforums.org/showthread.php?t=254061](http://ubuntuforums.org/showthread.php?t=254061)

---

### Post by Abstract on 2006-09-10
It is possible. This is how I think it would be done which is **highly unrecommended and I don't think you should do**.

```
sudo passwd root 
--
Enter password twice
--

```

Go to System -> Administration -> Login Window -> Security -> Allow local system administrator login -> Close

Now try and login using the username 'root' with the password you entered. If I explained this right you should have permissions to do anything and be as unsecure as you like. I hope I explained it wrong.

---

### Post by lodbergs on 2006-09-10
Once again I'm absolutely stunned by the helpfullness on this board AND by how fast you get and answer.

Thank you very much. 

I'll set it to auto login and nothing else. Once again thanks.

/Søren

---

