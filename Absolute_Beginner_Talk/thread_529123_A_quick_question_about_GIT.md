---
title: "A quick question about GIT"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by isaacj87 on 2007-08-18
Now I know that the question is partially about Compiz Fusion, but I figured this to be more related to GIT and the GIT Pull command.

I used a script installs Compiz Fusion automatically. It gets the source from GITWeb and compiles and installs...Compiz Fusion installed correctly, and everything is working fine, but whenever I do an update...**how do I know if it is actually updating**?
If I say "yes", then it will compile and the say "Already up to date." And if I say "no", then sometimes it says either "Already up to date" or appears to be downloading something. Then I go back and say "yes" to the ones that appeared to be downloading something...and it compiles, installs and says "Already up to date."

Is there a way to check that my version is the latest and greatest? I tried the individual folders and the Changelogs, but nothing has been written in them...

Here's a sample from the script itself:

```

cd ~/compiz/compiz
git-pull
read -p "Would you like to update Compiz Fusion?(y/n):" answer;
		if [ $answer = y ] ; then
			./autogen.sh --disable-kde && make && sudo make install
				else
				echo "Skipping..."
				fi

```

I don't know, maybe I'm being paranoid...it just doesn't feel like it is updating...:confused:

---

### Post by AlexenderReez on 2007-08-18
i noticed the script....hm...actually it has a lot of redundant question...asking stupid question..i guess you should modified that like that update script...that ask yes or not after git pull...which is after download any up to date compiz package...obviously the rules of git if it is up to date that it will tell you it is up to date...then , why the script asking do you want to upgrade ?of course we want to upgrade and that why we run the script ...that is just example unnecessary question.... 

to modified it...
refer

> [http://forum.compiz-fusion.org/showthread.php?t=1985](http://forum.compiz-fusion.org/showthread.php?t=1985)

---

### Post by isaacj87 on 2007-08-19
Bumping for more responses.

---

