---
title: "Newb need help with ut goty error"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by lildevil23 on 2008-02-21
Ok my problem is I'm a newb to linux, I hate to admit but I was using windows for to long and got used to working with it doing everything for you.  Windows now has givin me nothing but problems, I bought a laptop the ASUS EEE pc I love it. The only problem I'm having is I'm command shell illiterate, I have a friend who is trying to help me but our work schedules are way different so I need some help. 

What my problem is I know for a fact that ut goty runs on my laptop, cuz my friend has the same laptop, and he has it running on his, so I have it on my laptop and I made the ut file executable and try to run it I get "Couldn't run Unreal Tournament (ut-bin). Is UT_DATA_PATH set?" there are  alot of answers out there Ive tried a couple of different things changing the text script for the ut file that I found in this forum [http://www.linuxquestions.org/questions/linux-games-33/couldnt-run-unreal-tournament-ut-bin.-is-utdatapath-set-238010/#post1216070](http://www.linuxquestions.org/questions/linux-games-33/couldnt-run-unreal-tournament-ut-bin.-is-utdatapath-set-238010/#post1216070) 
about editing the text, I did that and I still receive that message. I'm dumbfounded by it, any help would be appreciated and if at all possible please explain in lehman's terms.  Thanks

---

### Post by freelinuxhelp on 2008-02-21
Do you know what the variable should be set to?
if you do, just run this at a command prompt:
UT_DATA_PATH='/path/to/executable'

include those single quotes

---

### Post by lildevil23 on 2008-02-21
ok I tried it and nothing then I tried typing it with sudo and I get 
sudo: UT_DATA_PATH=/path/to/executable: command not found
I dont understand why. I know where its at, its at /home/user/games/ut/ut/ut

---

### Post by freelinuxhelp on 2008-02-21
I'm sorry I wasn't very clear. When you run it, it just sets a variable. It won't give you any output afterward. If you want to check that it has been set correctly, run this:
echo $UT_DATA_PATH

And it actually looks like it might be looking for a directory.

---

### Post by lildevil23 on 2008-02-21
ok after I typed both of them like this
UT_DATA_PATH=/path/to/executable
echo $UT_DATA_PATH
it cam back with 
 /path/to/executable

---

### Post by freelinuxhelp on 2008-02-21
You would actually need to substitute /path/to/executable with /home/user/games/ut/ut
or wherever your data files are.

---

### Post by lildevil23 on 2008-02-23
sorry for the last response had to work 24 straight hours seemed like. Stupid question how would I go about changing the data path, and another question I have both install disks would it be a less hassle to try and install that way and how would I go about doing it. I mean I'm just looking for the easier route. What would you do.

---

### Post by freelinuxhelp on 2008-02-23
I don't know what the data path should be set to, but I've given you the command to set the variable. Once you know what the data path variable shoud be set to, no matter where it is, just assign the variable.

As far as what I would do, I'm not a gamer, so I would probably forget about UT and pick up a book on Python programming, Cisco networking or Bash scripting. :-)

Seriously though, you'll need to know what the data path variable should be set to before you can make UT work.

---

### Post by freelinuxhelp on 2008-03-08
Ever have any luck with this?

---

### Post by lildevil23 on 2008-03-08
No not really Ive been having to work to much to try anything lately. this is my first day off in awhile. so im back to working on it.

---

