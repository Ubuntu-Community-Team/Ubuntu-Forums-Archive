---
title: "Problem With Compiz And Gnome Compiz Manager"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by elektr10 on 2007-07-11
Hello,

I'm having trouble with the items in the thread.
Firstly, I installed CompizConfig Manager.There was no problem and the cube was rotating.When I restarted ubuntu, the cube disappeared.Then I learned that it's necessary to install Gnome Compiz Manager and installed.Everything was ok.I changed some settings in Gnome Compiz Manager and the cube disappeared again.

After uninstalling both of them,I installed CompizConfig Manager and the problem seemed till installing Gnome Compiz Manager.The cube disappeared again ](*,)

Please help me.

---

### Post by elektr10 on 2007-07-11
I realised that I missed that part during installation
> add this as two separate entries in the startup sessions:
Code:

System >> Preferences >> Sessions

Click 'new' and make its name: Compiz
And make its command: compiz --replace

And make one more:
Name: Emerald
Command: emerald --replace

Now just logout, then log back in, and BOOM! Shiny desktop effects!

Every session I enter "compiz --replace" the cube works well.But shouldn't it start on startup after adding it startup sessions?

---

