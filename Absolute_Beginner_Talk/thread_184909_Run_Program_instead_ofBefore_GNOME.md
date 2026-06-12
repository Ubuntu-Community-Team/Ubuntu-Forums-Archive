---
title: "Run Program instead of/Before GNOME?"
date: 2006-05-30
forum: Absolute Beginner Talk
---

### Post by featherking on 2006-05-30
Hello all,

I was wondering if this is possible. I would like to have a program run and no other programs. This computer will be placed in a public place and i was wondering if it were possible to just have it run a program instead of loading up a desktop. In windows this can be accomplished by replacing the shell 'explorer.exe' to whatever program you like. Is there a similar function in Ubuntu? 

I want the users to use this program only.

Thanks

---

### Post by ProjectGod on 2006-05-30
hmmm quite interesting... a computer in kiosk mode! i have no idea how you might do this... but i am interested in doing it on a windows machine... what do you mean by replacing the explorer.exe chell? do you mean editing the registry?? please explain! please share the knowledge!

:mrgreen:

---

### Post by featherking on 2006-05-30
You could have it be on a per user basis too,

It was somewhere in the registry in windows. I want to say it was HKEY Current User\Software\Microsoft\Windows NT\CurrentVersion\WinLogon and then you could add a key like Shell="your kiosk program here". I cant remember exactly what the key was that you added.. But if you do that, when that user logs in it would load right into whatever program except explorer.

The awesome thing is, if you ever do need to use explorer (you being the computer owner/operator) you could run the task manager and type 'explorer.exe' in the new task window and *bing* you have a fully functional windows. However, next time that user logs in it goes right back to your kiosk program.

Thats what im trying to do in Ubuntu, i think the performance will be much better in Ubuntu (its an Arcade Cabinet) because windows hogs all the memory by itself (older computer) So i was looking for other options.

---

### Post by featherking on 2006-05-30
Just Checked,

Thats Where it is  HKEY Current User\Software\Microsoft\Windows NT\CurrentVersion\WinLogon 

Then you add a String name "Shell" with the value to your program that you want to load

i.e.  Shell = "C:\Program Files\Internet Explorer\iexplore.exe"
will give you a kiosk where the only thing that happens upon login is that Internet explorer loads and they can only surf the net.
To disable simply rename the key to something like "(delete)Shell" or simply delete the key entirely.

Now if only i could achieve the same in Ubuntu, i find it hard to believe that Windows would allow me to do something Ubuntu cannot...

---

### Post by ProjectGod on 2006-05-30
excellent! cheers for that! hope ubuntu also has the same capabilities :D

---

