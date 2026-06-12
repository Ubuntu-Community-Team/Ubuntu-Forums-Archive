---
title: "[SOLVED] Cannot delete folder."
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by suomalainen on 2008-02-20
Ubunteros!

I have a folder with a single file inside. I want to delete both file and folder.

When I select either the file or folder for deletation I get the following error message:

[COLOR="Red"]Cannot move file to trash, do you want to delete immediately?

The file "2005.02.24 U.S." cannot be moved to the trash.[/COLOR]

So what can I do to get rid of these?

Thanks everyone!!!!

---

### Post by bschleusner on 2008-02-20
Did you click "Yes", that you wanted to delete it instead of moving it to the trash?

Also, under the file browser settings (Edit->Preferences), you can choose it to always show "Delete" so that when you right click a file you can directly delete it instead of moving it to the trash.

---

### Post by suomalainen on 2008-02-20
bschleusner, thanks for the advice but this didn't help. Do you have any other suggestions?

---

### Post by bodhi.zazen on 2008-02-20
Sounds like a permissions problem :

[http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

You can run nautilus as root, but be careful :

```
gksu nautilus
```

Or you can delete the file / directory in a terminal with sudo :

```
sudo rm -rf /path/to/delete
```

Again, be careful with that.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

gksudo : [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by suomalainen on 2008-02-20
bodhi.zazen , thanks for the advice. When SUDO is used is it 100% certain the file will get deleted?

The folder I had contained 100+pictures in it. For some odd reason only one pic could not be deleted. I did everything I knew possible to delete it and nothing worked.

Then I got the idea to go to the album these pics came from and copied a pic from the same folder to my desktop.

Then I renamed this pic to the same name as the pic I could not delete.

I then proceeded to copy this pic into the folder containing the pic I could not delete. I was asked if I wanted to replace it and I confirmed.

Then I deleted that sucker from my life for good! Ha!

---

### Post by bodhi.zazen on 2008-02-20
Woot ... :guitar:

Please mark this thread as solved, it saves the time of many volunteers looking to help ...

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by suomalainen on 2008-02-21
Although I mraked this post as SOLVED, I do believe I asked a question about SUDO that yet remains unanswered.

So were my questions answered.?

---

### Post by bodhi.zazen on 2008-02-21
Well, thank you for that. Your origional question (the title of the thread) was answered.

IMO if you have additional questions best start a new thread. It is unlikely you will get an answer to a sudo question in a thread titled " Cannot delete folder".

See the links I gave you on sudo and if you still have questions feel free to ask.

I can not tell from your description why you had issues with the single file in question.

---

