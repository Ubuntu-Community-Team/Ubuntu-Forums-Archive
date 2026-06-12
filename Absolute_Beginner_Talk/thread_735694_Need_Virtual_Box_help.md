---
title: "Need Virtual Box help"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by oblivioncth on 2008-03-25
I am planing to virtualy boot windows 98, ( it is second edition but that doesn't really matter) because I like that version, and Me because it is unstable (testing).

So I put the Windows Install disk in yesterday and said copy disk. I made an ISO in my home folder in some sub folder. So today Im thinking yay I get to see my favorite version of windows. But not so fast. I clicked new to add the OS to the list. Then I went to run it. It asked for a way to run it so I clciked CD drive and Image file and then selected the Image.
Then I clicked OK and got the error in the screen shot. It said something about permissions but I'm not sure how to do what it needs. 


On the screen shot you cant see the result code so im pasting it here:


Result Code: 0x80004005
Component: Console
Interface: IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

---

### Post by OmahaVike on 2008-03-25
it appears as if you need to add your user to the vboxusers group.  

system -> administration -> users and groups -> groups tab

find a group called vboxusers and add your user account to that group.  if, in the unlikely event, you don't have a vboxusers group, you'll have to create it.

---

### Post by glennric on 2008-03-25
Try typing
```
sudo /etc/init.d/vboxdrv start
```
in a terminal.  If this gives errors post them here.  If not then try starting the virtual box machine again.

Edit: Do this is what OmahaVike said doesn't work, although I think he has the right solution after looking closer.

---

### Post by overdrank on 2008-03-25
> **oblivioncth said:**
> I am planing to virtualy boot windows 98, ( it is second edition but that doesn't really matter) because I like that version, and Me because it is unstable (testing).

So I put the Windows Install disk in yesterday and said copy disk. I made an ISO in my home folder in some sub folder. So today Im thinking yay I get to see my favorite version of windows. But not so fast. I clicked new to add the OS to the list. Then I went to run it. It asked for a way to run it so I clciked CD drive and Image file and then selected the Image.
Then I clicked OK and got the error in the screen shot. It said something about permissions but I'm not sure how to do what it needs. 


On the screen shot you cant see the result code so im pasting it here:


Result Code: 0x80004005
Component: Console
Interface: IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}
HI you can
go to systems>administration>users and groups
type your administrator password
select manage groups,look for the group VBOXUSERS,
select properties and check the box in front of your user name.
Or use this command
```
chmod 660 /dev/vboxdrv
```
And always the user manual
[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)
Edit to slow :P

---

### Post by smurphy_it on 2008-03-25
Yeah I had this problem earlier today.  If you are running Ubuntu (gnome) in the system bar on the right hand side you should see the name of the logged in user (aka User Switcher).

RIght click on that and choose "Edit users and Groups".  Then click Manage Groups.  Scroll down to the bottom of the list and choose the vboxusersgroup.

Click a checkbox by your name in that window to make you a member of that group.

Log out of X-windows, then log back in.

That should solve your problem.

Looks like some other's beat me to the punch line here!

---

