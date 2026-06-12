---
title: "Alacarte - Adding a menu item problem"
date: 2006-08-17
forum: Absolute Beginner Talk
---

### Post by scweston on 2006-08-17
Hi,

I've recently installed Google Earth, which I have to say is pretty damn amazing!!! However, my only gripe being that it didn't add a menu item. The only way i can load it at the moment is to type 'googleearth' in to a terminal.

I'm trying to use Alacarte menu editor to add Google Earth. I use this method: -

Click Application>Accessories>Alacarte Menu Editor

I select the part of the menu I wish Google Earth to appear in (at the moment i'm trying to put it in 'Internet'). Then I click File>Add>New Entry and fill in the relevant field... i.e Name: Google Earth, Command: googleearth.

Once I've done all this I close Alacarte expecting to see the new item in my menu, however, it just doesn't appear at all! I've tried several times varying the basic method above in probably quite trivial ways, but never any luck.

Please could anybody help me out with why my new menu items just don't appear!


Also, would like the say huge thanks for this excellent forum and all the great people on it. Already as a relative newbie i've installed ubuntu to boot from a external USB drive, got wireless with WPA working, installed proprietary ATI drivers, got realplayer installed (so i can use the bbc website to watch their streams) and also got Google Earth installed. Please all keep up the hard work.

---

### Post by ComplexNumber on 2006-08-17
have you clicked on the left hand side of the new entry to make it visible?

---

### Post by scweston on 2006-08-17
> **ComplexNumber said:**
> have you clicked on the left hand side of the new entry to make it visible?

Thankyou for your quick reply.

Yep... that seems to be ticked automatically after i've completed the New Item dialogue. But doesn't seem to have any affect.

---

### Post by ComplexNumber on 2006-08-17
alacarte can be a bit funny sometimes. btw when you run alacarte, is the entry there? so what you're saying is that its in alacarte, but its not appearing in the menu?
also, did you assign an icon (note: not that this would stop it appearing in the menu)?

---

### Post by scweston on 2006-08-17
Well, the new entry appears in Alacarte after I have just added it through File>New Item dialogue. It even has the visible tick next to it, but when I close Alacarte the new item doesn't appear in the menu.

When I restart Alacarte to check the item I just added is still there, it isn't. It just dissappears as if I never tried to add it in the first place.

---

### Post by scweston on 2006-08-17
Sorry, with regard to the icon: in the various variations of attempts I'v tried I have attempted to add an icon. I used the one in /usr/local/google-earth/googleearth-icon.png.

I have since tried to reinstall Alacarte through the synaptic package manager. All with no luck.

---

### Post by ComplexNumber on 2006-08-17
> **scweston said:**
> Well, the new entry appears in Alacarte after I have just added it through File>New Item dialogue. It even has the visible tick next to it, but when I close Alacarte the new item doesn't appear in the menu.

When I restart Alacarte to check the item I just added is still there, it isn't. It just dissappears as if I never tried to add it in the first place.
that makes more sense. i've never known any instance of an entry appearing in alacarte but not appearing in the menu.  it seems strange that it disappears. i suggest that you may be doing something wrong, but i haven't worked out exactly what yet :)

i'm going to add a random application to the menu, so try to follow the steps for the entry that you want to add.

1) open alacarte and highlight the catagory (eg accessories, games, graphics, internet, programming, etc) that you want to add the item to

2) go to File in the menu and select New Entry.

3) fill in the details

4) check that it shows up in the correct catagory and close alacarte

5) check that it appears in the menu



don't worry, i'm not being condescending to you or anything by going through these simple steps. i just want you to do exactly as i do to successfully add an entry to the menu. if it works for me, then it should work for you. if it doesn't...if it doesn't, well, we'll have to take it from there. but i really can't think of any reason why it should disappear from alacarte of its own accord.
let me know how you get on.

---

### Post by scweston on 2006-08-17
No, don't worry about being condescending, I appreciate the help! To be honest I'm completely flumuxed by it, I'm very new to ubuntu, so trying to follow instructions to the word when I get them anyways. Although, would consider myself an advanced MS Windows user. Don't know if that's a help or a hinderence.

Tried your instructions exactly, but same problem. This time i took screen shots during the process. If there are anyways I can send the picture/ upload them I will

---

### Post by scweston on 2006-08-17
Some more information from playing around with it...

I don't think the problem is specific to adding new items. I tried modifying other items already there, such as names, comments, icons. I also tried ticking some of the items that don't have ticks by them. None of these changes seems to take affect after i've closed Alacarte.

When I restart alacarte it's as if i never made those changes. Could this be an issue with alacarte not saving the changes i'm making? Would this be a file permissions issue regarding which ever config file is responsible for the menu? How would I go about checking this out or fixing this.

Again thanks for helping.

---

### Post by ComplexNumber on 2006-08-17
i really don't know what the problem could be. i'm wondering if its something to do with file permissions in your home directory. maybe they have been changed somehow...although i can't think of any good reason why. ok, try this.....
1) go to /home/<your-username>/.local  (the '.' files are hidden files. to see hidden files, open nautilus, go to EDit -> Preferences -> 1st tab -> tick 'Show hidden and backup files'.

2) open up the terminal so that you are in that directory. (the command prompt should say: [your-username@localhost .local]$ )


3) type in 'chmod -R 700 *' (this will give all files read, write, and execute permssions for you, but noone else (except root))


i'm betting that you haven't got read access. how it became like that, i don't know.

now try to add the entry to alacarte.

let me know how you get on.

---

### Post by scweston on 2006-08-17
I have tried to follow your instructions above, but seem to have a few problems doing so. I open the terminal and try to go to the directory you ask me to, but this happens: -

stephen@ubuntu:~$ cd /home/stephen/.local
bash: cd: /home/stephen/.local: Permission denied
stephen@ubuntu:~$

I suppose this probably suggest that we're right to think it's a permissions issue though.

---

### Post by scweston on 2006-08-17
posted in error... ignore

---

### Post by ComplexNumber on 2006-08-17
> **scweston said:**
> I have tried to follow your instructions above, but seem to have a few problems doing so. I open the terminal and try to go to the directory you ask me to, but this happens: -

stephen@ubuntu:~$ cd /home/stephen/.local
bash: cd: /home/stephen/.local: Permission denied
stephen@ubuntu:~$

I suppose this probably suggest that we're right to think it's a permissions issue though.
problem solved! thats where new items are added to the menu. so we now know the reason why its not letting you. ok, try going to the level above (ie /home/stephen). now type in 'sudo chmod -R 700 /home/stephen/.local/*' ), then your password. then type in 'sudo chown -R stephen:stephen /home/stephen/.local/*'. if that doesn't work, try 'sudo chown -R stephen:users /home/stephen/.local/*'. 

i really don't know how you permissions have changed from your own. btw using nautilus, right click on /home/stephen/.local, select Properties, then Permissions. at the top, it will give you the file owner? does it say "root" or "stephen"?

the problem is either that somehow the permissions have changed so that you haven't got read access or they have somehow changed to root as being the owner. it can only be one or the other or both.

now add the entry to the menu.

---

### Post by scweston on 2006-08-17
Thank you!!! Problem now fixed!

In the end I typed in to the terminal: -

stephen@ubuntu:~$ cd ~/.local
bash: cd: /home/stephen/.local: Permission denied
stephen@ubuntu:~$ sudo chmod -R 700 /home/stephen/.local
stephen@ubuntu:~$ cd ~/.local
bash: cd: /home/stephen/.local: Permission denied
stephen@ubuntu:~$ sudo chmod -R 700 /home/stephen/.local/*
chmod: cannot access `/home/stephen/.local/*': No such file or directory
stephen@ubuntu:~$ sudo chmod -R 700 /home/stephen/.local
stephen@ubuntu:~$ sudo chown -R stephen:stephen /home/stephen/.local
stephen@ubuntu:~$ sudo chown -R stephen:stephen /home/stephen/.local/*
stephen@ubuntu:~$

Lots of that was me not completely understanding what I was doing, but working it out myself...

This appears to have done the trick... again a big thank you for bearing with me and helping me through each stage of fixing this!

Think I will make file permissions in linux the next thing i learn about.

---

### Post by ComplexNumber on 2006-08-17
i'm really glad its worked out :). file permissions aren't difficult at all, but they are so effective when it comes to security. its one of the areas that really put *nix head and shoulders above windows for the foreseeable future when it comes to security.
i'm not too sure if [this]("http://en.wikipedia.org/wiki/File_system_permissions") helps about file permissions. i've seen much easier tutorials than this, though. it doesn't explain it as easy as it could be.

---

### Post by bushsux on 2006-08-25
I had the same problem, .local was own by root. The only thing under there were enteries for google earth install by automatix, might be a bug.

---

### Post by gumbald on 2006-08-28
Same for me, thanks for the fix :)

---

### Post by SentientFluid on 2006-08-29
ooops... nm :)

---

### Post by mtn on 2006-08-31
Same problem, after new install Dapper 6.06.1 386 desktop!

---

### Post by SentientFluid on 2006-09-01
> **mtn said:**
> Same problem, after new install Dapper 6.06.1 386 desktop!

I had the same thing happening and it was because my *.local* folder was owned by *root*. Everything was was fixed by doing the same thing Stephen did (which I conveniently repeated below):

```
sudo chmod -R 700 /home/**yourusername**/.local
sudo chown -R stephen:stephen /home/**yourusername**/.local
sudo chown -R stephen:stephen /home/**yourusername**/.local/*
```

---

