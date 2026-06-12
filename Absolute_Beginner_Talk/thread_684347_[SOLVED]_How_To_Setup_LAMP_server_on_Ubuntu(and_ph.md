---
title: "[SOLVED] How To: Setup LAMP server on Ubuntu(and phpbb3)"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by RadiationHazard on 2008-02-01
Ok, this if my first how to. So if i do something wrong just tell me I will try and fix it.

Ok, so for starters the whole reason I'm writing this how too is because i just installed a LAMP server onto my box and phpbb. And I had a really hard time with it because i was trying to follow other sites tutorials and they used terminal. Now don't get me wrong i love terminal and have nothing at all against it. but i learned the hard way that you should check synaptic package manager and add/remove programs first. because if you use synaptic or add/remove you're ensured that the packages will be installed correctly unlike with the terminal where it's easier for you to mess up somewhere.

So back to setting up your LAMP server. Got to System>Administration>Synaptic Package Manager. Then put in your password and when it comes up go to Edit>Mark Packages by Task... then it will open up something that looks like this

[[IMG]http://i32.tinypic.com/2nh0wf8.png[/IMG]]("http://i28.tinypic.com/szhkhx.png")
(click picture to enlarge.)

Now mark "LAMP server" as you can see I've done. Click Ok. then click apply. It will install the packages. While it's installing something should pop up asking you to set your mysql password. Make sure to set it as something that you will remember. When it gets done to make sure everything is installed correctly and working the way it should go to

[COLOR="Navy"][http://localhost/]("http://localhost/")[/COLOR]

Now that should take you to your Apache Directory. Now if everything is working right go to Synaptic Package Manager again (System>Administration>Synaptic Package Manager)
and now search "phpmyadmin" but without the quotes. One package should pop up.

[[IMG]http://i25.tinypic.com/n6sx1h.png[/IMG]]("http://i32.tinypic.com/14tbwcn.png")
(click picture to enlarge.)

Mark the package for installation and then click Apply. Once that is done installing to to 

[COLOR="Navy"][http://localhost/phpmyadmin]("http://localhost/phpmyadmin")[/COLOR]

and it should take you to this page

[[IMG]http://i27.tinypic.com/33wb3eo.png[/IMG]]("http://i28.tinypic.com/6z8nbk.png")
(click picture to enlarge.)

Now, for the username it should be "root". and then password is whatever you set your mysql password as remember I told you to remember that you'd be needing it! :)
ha ha. So any ways. Once you are logged in go to "Privileges" Then go to "Add a new User" in the "User name:" put whatever you'd like your username to be. Something that's easy for you to remember. then for the "Host:" click the drop down box and select "Local" it should also put "localhost" in the black. Then for the password type the same password you used earlier or one that you'll remember and then retype it. Where it says "Database for user" select the option that says "Create database with same name and grant all privileges" once you're done scroll all the way to the bottom and in the bottom right hand corner there is a button that says "Go" click it. It should take you to a new page and on that page it should say something along the lines of "New User Added." or something like that.

Now that we're done with that click [COLOR="Navy"][here]("http://downloads.sourceforge.net/phpbb/phpBB-3.0.0.zip?download")[/COLOR] to download phpbb 3.

for the options click "Save to Disk" and then ok. Save it to your desktop if it does not do that already. When it is done downloading extract the package to your desktop.

Now go to the terminal and type in 

```
sudo nautilus
```

this will bring up a window that looks like this...

[[IMG]http://i32.tinypic.com/29c7v2g.png[/IMG]]("http://i25.tinypic.com/dvom6d.png")
(click picture to enlarge.)

Now click File System then open the folder in there called "var" and then the folder in there called "www" there should be a folder in there that says Apache-2 or something along those lines. Delete it. you don't need. That is not actually your Apache. It's just the  index file that comes with it.


Now on to setting up phpbb3. Go to he folder that you downloaded. Extract it to you desktop and then enter this command into the terminal again if you've already closed that window that had opened 

```
sudo nautilus
```

then go to your severs folder. (File System>var>www) and open the phpbb3 folder, copy all the folders that are in it and cut and paste them into your servers folder. Now minimize all that and open your browser and go to [http://localhost/]("http://localhost/") again and it should bring you to the phpbb3 installation page. Now click the install tab. It will take you to the introduction then go to the requirements. If you did everything right you will meet the requirements so scroll down to click the button at the bottom and continue to Database Settings. For the "Database server hostname or DSN:" put "localhost" then for the "Database server port:" just leave it blank. You don't need to file that in. Then for the "Database name:" and the "Database username:" put the name that you mad in phpmyadmin that i told you to remember. now for the password put the password that you made in phpmyadmin. Now that you're done filling all that out click proceed to next step. Put in your administration details. That's all up to you. Now that you've set up the administrative stuff you come to the spot where it says download config.php file. download that file to your desktop. Go to you desktop cut it and past the file in your servers root folder(www folder) a pop up will come up saying that there is already a file in that folder with at name it will give you the options of skip or replace. Select replace. Now close that file. Unminimze your browser and click done. Now for the rest of the set up it's just pereference. The way it is set was fine for me and will probably be fine for you too,

Now that you're done with the set up. Open your terminal again and type the 

```
sudo nautilus
```

in one last time to complete the set up. Go to your servers folder.(File System>var>www) and delete the folder that says install. Now close that window and you're done. Phpbb3 in now completely installed. you're free to edit it and make it like you want. Enjoy your new site and please post feed back on this. Sorry if it's not the best how to but at least i tried right? :)



-RadiationHazard

---

### Post by RadiationHazard on 2008-02-01
is this a bad how too or something? :(

---

### Post by deeef on 2008-02-02
hey, its a good tutorial, I just followed it to install LAMP on my new ubuntu desktop.

thanks :)

---

### Post by JoshuaRL on 2008-02-02
Sweet dude.  You might repost it in this forum for more traffic of those who know about it:

[http://ubuntuforums.org/forumdisplay.php?f=7](http://ubuntuforums.org/forumdisplay.php?f=7)

---

### Post by jackwhite on 2008-02-18
weird. When i go to Synaptic and do the following: 
```

>System
>Administration
>Synaptic Package Manager.
>Edit
>Mark Packages by Task

``` 

I am only presented with two options: 'Print server' and 'Ubuntu desktop'.

Both are greyed out and cannot be unselected or even installed (presumably because they're already installed).

Any ideas?

---

### Post by om1 on 2008-02-18
one thing you could change... not that it is wrong... instead of opening terminal and typing sudo nautilus you could press alt+F2 and type gksudo nautilus and press enter... then type your password and boom root nautilus

---

### Post by jackwhite on 2008-02-18
Ok, I see that this was also posted to another area where there's been some discussion: V

I'll repost my query to there.

---

### Post by Rock` on 2008-02-20
Hey guys, 

I install Apache/mysql/php/phpmyadmin seperately using sudo apt-get install, LAMP is ticked already in the edit > mark tasks part.

My question is this, when going to localhost, I can get to the apache directory just fine, however, I can't get into phpmyadmin, it says it doesn't exist, although ubuntu says the package is installed.

Any ideas?

---

### Post by BrentC on 2008-02-23
My problem is after everything is setup, I can't view an page as a PHP enabled page.

ie; It just shows the php code, rather than the GUI that should show up on those phpBB3 pages. :(

---

### Post by Usta_AsH on 2008-02-23
Site error: the file xxxx requires the ionCube PHP Loader ioncube_loader_lin_5.2.so to be installed by the site administrator.

---

### Post by adredz on 2008-02-25
Hi,

@RadiationHazard

Could you post the terminal way? I just wish you could. I hate package managers...

Thanks!:)

---

