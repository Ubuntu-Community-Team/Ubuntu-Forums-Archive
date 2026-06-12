---
title: "user default language"
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by JanLimpens on 2006-09-14
is it possible to configure ubuntu, so that different users have different gui languages (betty gets english, zico gets portuguese,...) without having to meddle with the login options every time they log on?

---

### Post by kazuya on 2006-09-14
I'll have to try that. I figured, maybe you would first install the languages. Log in as the separate users, but at login for each one, you set the language, and pick a greeter bootsplash that shows user names for login.

I'll investigate. Any ideas from the rest of you great admins and users? I am a rookie in this department.

---

### Post by JanLimpens on 2006-09-14
Thanks a lot for looking into it. Right now I have to click Options/Set Language/Select the language from a long list/Confirm selection as non-standard everytime I log in. Gets boring after a little while ;).

Jan

---

### Post by michael117 on 2006-11-23
I know this thread is a bit old, but I was looking to do the same thing and figured out how to do it.

If you go into the terminal and type "cat /etc/environment" you will see it print out a "LANGUAGE=" option and a "LANG=", highlight these, right click and copy them. Then cd to whoever wants the different language's home directory and type "sudo .bashrc". This will open up and find the first empty area underneath the commented lines at the top and paste the two things copied from the /etc/environment file. Although, you must edit the two to fit whatever language you want. Not sure what the specific locale name for Portuguese is, but if you aren't sure then try messing around with the current setting. For example, I was looking to set my dad's account up to be in Polish, so I configured the two as LANGUAGE="pl_PL:pl" and LANG="pl_PL.UTF-8". If you aren't sure then type "ls /usr/share/i18n/locales/" into the console and it should give you an entire list of possible locales or try "ls /var/lib/locales/supported.d" to see what you have installed but it isn't in the necessary format to put into the .bashrc file. Save the .bashrc file if you haven't already and go test it out!

If it doesn't work right away, then there were a few other commands which I typed in but I thought weren't important. I tried typing in "source /home/*user*/.bashrc" but I accidentally did that while I was in my account and everything became Polish. I also typed in "env-update" but it didn't seem like this made a difference in getting it to work, so it isn't in the instructions.

---

