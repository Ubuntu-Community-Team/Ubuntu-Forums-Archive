---
title: "Installing PHP?"
date: 2005-07-17
forum: Absolute Beginner Talk
---

### Post by wonderland on 2005-07-17
Hi every one, i have used ubuntu for 2 days including now, i spent yestarday trying to find out how install my modem which i finally did. Now i want to start coding PHP. My problems are listed below : -

1) I installed apache well i think i did, but the folder /var/www/ is not writeable, i cannot create any folders or copy and files in there. Oh yeah and there seems to be a folder called "Apache2-default" in there also, which is not writeable. I know that this folder is the localhost location.

2) How do i install PHP, PHP5 prefered. Also how do install MySQL and phpMyAdmin.

What i really want to know is how to install the whole thing so i can start coding. Please some one help, and if anyone can, can you please give instruction step-by-step.

Oh yeah iv also tried out that "Unofficial Ubuntu 5.04 Starter Guide" (from [http://ubuntuguide.org/](http://ubuntuguide.org/)) and where it says "Q: How to install PHP for Apache HTTP Server?", it tells me to enter this in to the terminal, (iv tried both terminal and root terminal):

sudo apt-get install php4
sudo /etc/init.d/apache2 restart
sudo gedit /var/www/testphp.php

This is what i got for typing in"sudo apt-get install php4":

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package php4


Someone help please?  :???:

---

### Post by dave9191 on 2005-07-17
The dir is not writeable to you, but it is writable to the owner / root. So when you copy files in there use the sudo command. An alternative is to make it globaly writable, but thats a massive secuirty issue. And in the apache config you can set up a folder in your home dir (localhost/~username) and make a folder in your home dir called public_html. Im not sure if this is a default setting in apache with ubuntu or not. 

As for installing using the instruction from ubuntuguide, did you follow the two points?

# Read General Notes
# Read How to add extra repositories?

I'm guessing that you didnt bother to add the extra repositories and therefore apt-get cant find the stuff. 

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

If you want to install php 5, then you'll need to compile it yourself. I tried that the other day and I run into all sorts of configuration issues. I'm going to try and sort it out one day, there must be guides online about how to do this anyway. 

Dave

---

### Post by wonderland on 2005-07-17
if it helps, in the Synaptic Package Manager, under Settings > Repositories, there is only ONE. And that is "CD Ubuntu 5.04 Hoary Hedgehog (binary)".

---

### Post by smoon on 2005-07-17
[QUOTE=wonderland]if it helps, in the Synaptic Package Manager, under Settings > Repositories, there is only ONE. And that is "CD Ubuntu 5.04 Hoary Hedgehog (binary)".[/QUOTE]

You should read the "[Unofficial Ubuntu 5.04 StarterGuide](http://ubuntuguide.org/)"'s section about "[How to add extra repositories?](http://ubuntuguide.org/#repositories)".

---

### Post by wonderland on 2005-07-17
just adding them now...Reading Package Lists... Done

---

### Post by wonderland on 2005-07-17
Im installing, Im installing, Im installing, Im installing,  \\:D/  YESSSssssss ..... better not get too carried away, especially with Linux. Oh whilst its installing and as fast as your replies are (appreciated) can any one tell why i have too keep configuring my modem sagem fast 800. every time to connect to the internet. if i dont it says modem unoperational or something like that,

---

### Post by wonderland on 2005-07-17
what is the GNOME panel and why does it need to be refreshed?

---

### Post by dave9191 on 2005-07-17
I dont know about your modem, But to save time you might want to write a script to configure it for you rather then doing it by hand. 

And the gnome panel is what you see at the top and bottom of the screen in gnome (where the menus, tasks, clock, bin, desktop switcher are all on). it needs to be refreshed so that you can see any changes that are made to it. And it should refresh automoatically rather then you having to refresh it manually. 

Dave

---

### Post by wonderland on 2005-07-17
hi dave thanks alot, but now i have another probem i reading the manual and im upto the bit "Q: How to install MYSQL for Apache HTTP Server?" when i type "sudo apt-get install libapache2-mod-auth-mysql" an error occurs. Any way i think this means that i need to create a server us mySQLCC but i cant connect to server. I try localhost as the host name and root as the username with my password i use for my system and still it says "[wonderland] ERROR 1045: Access denied for user: 'root@localhost' (Using password: YES)" please help becuase this is one of myy final steps to start coding PHP!!!! thanks alot dave and everyone else  :)

---

### Post by dave9191 on 2005-07-17
Have you installed apache, mysql and php in the way and same order as ubuntuguide tells you to. And what error occurs?

Dave

---

### Post by wonderland on 2005-07-17
well it works now for some reason but anyway... (thanks by the way for caring) but anyway... 

"How to map URLs to folders outside /var/www/?"<---  What does this section mean and why do i need to do this. does this mean i can make this a writable folder. and if not can you please tell me how to make it a writable folder, and also can you make writable through GUI mode? thanks this is the last question.





well actually maybe not i might need to ask you how to write that script for the modem thingy.

---

### Post by dave9191 on 2005-07-17
When you go to localhost it will display whatever files are inside /var/www (thats the directory that apache uses by default to store webpages. 

Now if you create a folder foo inside /var/www/foo, you can access the files inside there by going to localhost/foo. But if you want to store the files for foo somewhere else (possibly /home/user/foo) you can add an alias for that in the configuration file as discribed in that section of ubuntguide. Once thats done and the server is restarted going to localhost/foo will read /home/user/foo instead. 

As for making a folder writeable you can do that wither with the command line or a gui. Im guessing that you use gnome, and I dont so i can give you step by step instructions. But you would have to start the file browser as root and then rightlick on the folder you want to make writeable and go to propeties. 

On the command line you could do something like 

sudo chmod 777 /var/www

THIS WOULD BE VERY VERY BAD if your system is accessible to the outside world on the net. Best to either use an alias or localhost/~username. Try making a folder in your home dir called public_html and make that readable to everyone. and access it throught the browser. 

As for making the scipt to configure your modem, you would need to find the command line commands to set it up by and put them into a text file and make that exectuable. 

Dave

---

### Post by wonderland on 2005-07-17
thanks dave its a bit clearer now but erm, what do you mean by :

" Try making a folder in your home dir called public_html and make that readable to EVERONE. and access it throught the browser. "

isnt that bad im mean so that every one on the net can see it. oh or do you mean "Owner" , "group" and "others" can see it. but who are the "others" and arent i logged in as the owner anyway so why cant i write on it.

as for the alias i will do that and create a folder on desktop but first i think i need to understand the above information first.

thanks

---

### Post by wonderland on 2005-07-17
also you cant create an alias for a folder in var/www/ if you cant even create a folder in there. Its totally locked. How can i put things in var/www/ even the permmissions are locked and gray.

---

### Post by dave9191 on 2005-07-17
When i say everyone i mean a read for the owner, the group and others. And others being anyone else who isnt the owner or in the same group as the owner. And that is the only way that you will be able to see it while looking at the page in a browser. And thats the same for people on the net. Its up to you to make sure that your machine is firewalled and protected from the net if you dont want people accessing it from the outside world. 

You can run these commands if you prefer

cd ~
mkdir public_html
chmod 744 public_html


now put a file index.htm into public_html with some text and open a webbrowser and try localhost/~YOUR_USER_NAME

If that works, then you can develope your code there :) 

Dave

---

### Post by wonderland on 2005-07-17
Forbidden

You don't have permission to access / on this server.
Apache/2.0.53 (Ubuntu) PHP/4.3.10-10ubuntu4 Server at localhost Port 80


Thats what im now getting when i access localhost.

Also you know when it says copy these lines into the new file:

Alias /URL-path /location_of_folder/

<Directory /location_of_folder/>
   Options Indexes FollowSymLinks
   AllowOverride All
   Order allow,deny
   Allow from all
</Directory>

do i were it says /URL-path change that to local host or not. and do i also change where it location_of_folder put the location of public_html.

---

### Post by wonderland on 2005-07-17
now localhost dont work whatever i do. it stoped working when i did that section. shit some one (im guessing its you, know that your angry with me) deleted every thing in www/ folder. theres only two files now with both icons being a foot. ones called testingphp.php and another is called, apache2-defualt (with no extension).

please help

---

### Post by dave9191 on 2005-07-17
Did you try the public_html method before trying out modifying the config file for the alias? Or did you try and combine the public_html folder method with the alisasing method? Foribiden error will either mean you dont have read access for others on that files / folders or that you messed something up in the config file. 

Dave

---

### Post by wonderland on 2005-07-17
man dave every things gone wrong now, becuase var/www/ had one folder and one php file now there are only to looking weird files. That i never saw before how can i start from scrath, and dont understand what you even mean about method, becuase the point is that var/www/ is un writable i could not add anything in there not even create a folder, and also the config file, i didnt know to write the path of public_html, please tell me how to start from scratch.

---

### Post by dave9191 on 2005-07-17
you cant write to a folder outside of your directory unless you do it as root. Same applies to the config files. To start from sractch you would need to unistall all the packages and clear any of the config files that might be left behind. 

Try to remove any changes that you made to the config files. And restore whatever it is that you did.

---

### Post by wonderland on 2005-07-17
i dont even know how to even unistall them, i mean where do i go and under what name are they in, let alone redo a config file, i just been goin with the guide.

---

### Post by dave9191 on 2005-07-17
sudo apt-get remove package name

The you'll have to look through the /etc folder for the configuration files, they will probably be left behind. 

And when i say redo the config file just change back whatever you edited in it. Whenever you modify a config file you should always have a backup made first just in case. 

Dave

---

### Post by wonderland on 2005-07-17
what were the package names, i dont know that package names what packages was in that guide

---

### Post by dave9191 on 2005-07-17
Well to install the packages you typed

sudo apt-get install package_name

So Im guessing that you know the package names :) 

Dave

---

### Post by wonderland on 2005-07-17
1) i removed all the packages.

2) cant i just re-config the configuration files next time i install the whole process again.

3) for some reason those two weird files are still there, in var/www/ , here is a screen shot.

[IMG]Here is the screenshot[/IMG]

---

### Post by dave9191 on 2005-07-17
delete those as well. (and you have to do it as root)

Dave

---

### Post by wonderland on 2005-07-17
1) there not deletable through GUI, and i am a total newby to all this so the phrase "Do it as root" i dont have clue wat that means. Please explain or simply tell me how to do it in console mode.

after that do i leave the files or what becuase i cannot find them in that long folder, should i just leave them becuase the next installation will correct them(i think)???

thanks

---

### Post by wonderland on 2005-07-17
please help, how to delete that file through root, i think root means the root terminal in system tools but what is the command to delete them, and i dont know how to navigate in console mode, like in does mode its cd home, cd dekstop

please help i really appreciate everything.

---

### Post by dave9191 on 2005-07-17
Sorry man, but some of these are basic linux concepts. If someone tells you do something that you dont understand then look it up on google. There are pleanty of guides , and even recently i saw a post on the forums about running a file manager as root. 

In linux you log in as a user who only has access rights to his/her own home directory. The root (admin) user has full access to the system and can edit any file and write to any directory. And in ubuntu you can issue root instruction using the sudo command like you were told during install and if you need more info about htat its all in the wiki. 

When you look at it in a file browser that is running as you (your user name) then you wont have access to delete the files there. 

You can do everything with the command line if you wish, but it would be easier to run a file manager as root. Start it by typing 'sudo nautilis' (but you'll have to get the spelling of the program name right, i cld never remember it and i dont use gnome. hitting tab while typing in the console will auto complete for you. 

If you want a command that will remove all the files in /var/www then 

sudo rm /var/www/* 

I recommend that you read up some guides about using linux, it would make things a lot easier for you to pick and navigate. The sudo mean run as root. the 'rm' is the remove command. /var/www/* is the file to remove, in this case * meaning all. 

And navigating in dos mode and linux is similar, just some of the command are different. 

cd - change direcotry 
rm - remove file
ls / dir - list dir contents
mkdir - make directory 
rmdir - remove directory 

Installing the packages again will hopefully overwrite the existing config files, but if they already exist it might leave them in place. 

Dave

---

### Post by wonderland on 2005-07-17
I appreciate everything man. im currently trying to release my windows mind and learn some of this linux commands and stuff. So erm please dont try and hack into my computer again. thanks, those two files just finally got deleted by them selves some how right in from of my eyes as soon as i opened the folder one disappeared after the other, please tell me that was you hacking to my computer becuase ill be just confused thanks man.


thanks for every dave. im starting a tutorials website on photoshop. and ill defo credit you. but i need to use php for that anyways just respond by saying wether that was you or not.

thanks alot man.

---

### Post by wonderland on 2005-07-17
no wait now whats happened is that when i open www again, apache2-defualt is there only when i right click and open its properties, it disappears, and the testphp.php is gone completey some how. Do you think i should stick to windows becuase this is a nightmare and is really frustrating. how old are you by the way and how did you get into using linux if windows is so easy and just as powerful

---

### Post by dave9191 on 2005-07-17
No, it wasnt me hacking into your computer.... it was probably a deamon or some other process that removed them after you removed the packages. 

Im 21 and I got into using linux a couple of years ago when using unix solaris at uni. I was looking for something to easily ssh into university compuers. All the ssh client on windows werent as good and cygwin was unstable and not as nice. And all the viruses and adaware and other junk that sticks to windows just got on my nerves. A clean fresh install of windows with all sorts of scanner running in the background and I still caught viruses. I thought Id give linux a try and very soon I was hooked. 

Its so much more powerful and flexible then windows, not to mention more secure and faster. My laptop boots in 15 sec into fluxbox vs the 50 sec into windows. I dont waste reasources running virus scanners, ad ware scanners, spy ware scanners. In fact my linux setup uses far less reasources to do anything and is much faster. And its configured just like I like it. Keyboard bindings to open applications, multiple desktops, the list really goes on. 

The firewall is a simple config file more powerful then most windows firewalls. No need for virus scanners. Its just great. 

Also working with php and apache and mysql and a lot of other open source projects is better on linux rather then having to work with a buggy, poorly supported or out of date port to windows. 

Linux isn't that difficult, its just different to windows. If you are good in windows going to an OS were everything is different can be annoying and difficult. I made the transition with guides in the matter of days and in a matter of a couple more months I was doing things with linux that Ive never done with windows after 10 years of using it. 

Now when I go back to using windows I get very annoyed and fustrated when I cant do things that I consider basic in linux. 

Dave

---

### Post by wonderland on 2005-07-17
but dave what do i do now becuase it keeps coming back up every time i revisit www folder. Do you think if i re-install apache2 then it wll right over this shity file. becuase its annoying and i cant even change the permission of it in sudo, please at least give me a command to type in.

its a file and its not even a folder, it an unknown type (before it was a folder, i can remember that) Now its seems to just one object. and not accessable, yet i cant delete it in sudo. 

its in var/www/ the path for it is /var/www/apache2-defualt please give me a command to change the restriction of this so i can delete it and reinstall the php, i only have today to make the most of linux and hook my self onto it other wise i got driving lessens with dad tomorow and then ill give up with linux which is what i dont want to do, after this ill get a book on linux becuase these guides online are long and not even detailed enough.

please help please help... could i also have your email address to add you to my msn.


thanks man

---

### Post by wonderland on 2005-07-17
do you think if i reinstalled apache2 it will take it off and install over it.

---

### Post by dave9191 on 2005-07-17
Try installing the pachages again as described by the ubuntu guide and see if it works. If it doesnt then maybe the easiest thing for you would be to reinstall ubuntu and install them again, rather then trying to fix it. 

You can add me to your msn list if you want. dave9191 -- at -- hotmail.com. I prolly wont be online again till tonite tho. Im running out of battery now. 

Dave

---

### Post by spartas on 2005-07-17
wonderland, it will replace all the necessary files when you reinstall the apache2 package.  Just run 'sudo apt-get install apache2'.  You shouldn't have to mess with the config file for apache.  

Just create a new folder in your home folder called public_html and put your php stuff in there.  You will be able to access your stuff at the [http://localhost/~](http://localhost/~)[your_user_name] (don't forget the tilde ( ~ )before your username though).  You're also going to need the other packages as well (php4, mysql-server).

Use the following code to restart apache2:
```

sudo /etc/init.d/apache2 restart

```

---

### Post by wonderland on 2005-07-17
hi spartas i have just reinstalled everything including ubuntu, i understand that you need use sudo to actually write things in /var/www/ but the thing that i dont understand is how do i link the public_html folder to the unwritable www folder. Please  help i have literally spent all day trying this.

---

### Post by dave9191 on 2005-07-17
Have you tried as I suggested earlier, creating the public_html folder, chmod 744 it, put a basic html index.htm and then type into the browser localhost/~your_user_name. 

From what I remember its already setup in the default apache install to read from a public_html folder in your home dir. 

Dave

---

### Post by wonderland on 2005-07-17
iv been told on the mirc chat and they said to do this command: sudo chown chris /var/www/

this actually makes it work now, but isnt this a security issue of where any one can hack and access this folder. anyone from the internet i mean, like the people on the chat.

i think i never told you that i am the only user on this linux machine. or did you already now thank you. sorry if i didnt tell you.

---

### Post by wonderland on 2005-07-17
although i still dont understand your recent post, the thing about the public_html folder, please can create a step by step guide. on how to make public_html part of the webserver so i can use that instead of var/www/ also another question why was var/www/ already locked.

---

### Post by dave9191 on 2005-07-17
I already gave you a step by step guide on how to do this ealier in the thread,,, but here are the commands again...  and what do you mean by locked? 


Just do these one after another in a command line

cd 
mkdir public_html
chmod 744 public_html

Now Im guessing you know how to write a basic html page since you do php. So make one and put it in that public_html folder and call it index.htm. 

now back to the command line 

cd ~/public_html
chmod 744 index.htm

Now open a web browser (firefox or something) and type in the address localhost/~YOUR_USER_NAME

That should open the index.htm page you just created. 

Dave

---

### Post by wonderland on 2005-07-18
ok dave ill try that, but what i mean by the var/www/ folder being locked is that i cant create a folder in there or even create or copy a file in there, but i managed to give every permission to me, by doing this command which someone gave on the mirc chat. sudo chown sirwan /var/www/

now i done that i can actually creat files in there, but i still want to do the public_html file on dekstop so im going to do what you told me do on your recent post.

---

### Post by dave9191 on 2005-07-18
The /var/www folder is owend by the root user after install, because it was insalled by the root user (the sudo means run this command as root wheny ou installed it). You need to understand some of the basics about file permissions and ownership in unix. Look up some tutorails about it. Here is one, but I dont know how good it is. 

[http://www.dartmouth.edu/~rc/help/faq/permissions.html](http://www.dartmouth.edu/~rc/help/faq/permissions.html)

The chown command changes the ownership of a folder / file, and now that you changed to to be owned by you, you can write to it as normal. I should have suggested the chown option, but it didnt cross my mind for some reason. It doesnt cause any security issues either by others being able to write to that folder. 

Dave

---

### Post by wonderland on 2005-07-18
ok i know understand that but can you give me a step by step guide on the public_html now that i have reinstalled ubuntu. that text file you have to create and enter in the text what bits of that text do i need to change. In this section of the guide: "How to map URLs to folders outside /var/www/? "

What bits in this piece of text to i need to replace.:

Alias /URL-path /location_of_folder/

<Directory /location_of_folder/>
   Options Indexes FollowSymLinks
   AllowOverride All
   Order allow,deny
   Allow from all
</Directory>

the folder i want is in home/sirwan/desktop/public_html please write type in what the above text should look like for my specification

thanks alot dave, im trying to give u as much reputation.

---

### Post by dave9191 on 2005-07-18
With the public_html thing (like I mentioned in another post) you dont have to edit the configuration file becuase it should be set up already. Have you tried to access the html page you created and put into public_html through a web browser? If you did you would either see it or get an error. 

Dave

---

