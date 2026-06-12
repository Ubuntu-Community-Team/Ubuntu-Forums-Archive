---
title: "Session menu program doesn't behave properly"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by The_Marlboro_Man on 2007-11-27
Hi!.

I just finished coding a small application to be executed with each startup of my system: the application itself is a small organizer that writes and reads dates from a file and then reflects them on a calendar.

The problem is that when I add my application to the startup (on Ubuntu 7.10 with Gnome) the application itself does fire but it doesn't seem to read the file (the one that contains dates and information) at all!!. If I shut the application and fire it again it does work as intended.

I put my application in a directory inside my personal folder. This folder (not my personal, the application's) has permissions like "Create and delete files" for me and "Acess to files" for the rest. Trying to solve something I set the permissions for the files to be read to "Read and Write" for me, my group and everyone else... Still it doesn't work.

I guess the problem has something to do with the folder permissions or something (as the startup can't access them but I can) but the application doesn't show any "Access denied" message at all... What should I do to get the application running properly?.

Another question, as said, I put my application into a directory in my personal folder but, should I put it somewhere else?. Somewhere more, "standard", so to say?.

Thanks in advance.

Edit: I just noticed that on startup the application looks for the files in another folder... In the same folder as the "executable" there's a "Data" folder where data is stored. In startup I see that the application is trying to reach the "Data" folder as if it were inside my personal folder (it creates the Data folder as if it didn't exist). When running the program directly it looks for the "Data" folder where it should be... It is almost as if the application was run "from" my personal folder instead of its own folder... So to say, if I go to the console and do

cd Desktop
/home/myname/applications/calendar/calendar 

It creates the "data" folder in the "Desktop". I could try and correct this by specifying a path into one of those "usr" folders, completely unknown to me but again, I would like the program to be wherever the user wants and the "data" folder directly where the application is. How could I correct the startup behaviour?.

---

### Post by master_kernel on 2007-11-27
Try running the application alone from the terminal and see if it works. If it doesn't, either it is not executable (fixed by chmod +x program) or it is a program issue.

---

### Post by The_Marlboro_Man on 2007-11-27
Oh, it does run from the console without a problem. What I meant is that the application does indeed run at startup but does funny things with its "position". Let me explain that a bit... The application is done with Lazarus, in FreePascal. For each time the application starts it checks for the existance of '/Data' and creates it in case it doesn't exist... I thought that '/Data' meant "Look for data in the directory the executable is" but I am dead wrong in that as it does "look for data in the directory where the user is when calling the executable". Something like './data' just doesn't work in Lazarus and well, 'Data' alone had the same results...

Anyway, when running the application at startup it seems to run from my personal folder and, thus, 'Data' is stored right there... Could there be way of changing the "startup user location" for my application?. I don't know a lot about Ubuntu but the other options to me are:

-Create a script that goes into the program folder and then runs it. Run the script at startup... But well, I don't know about scripts, how would I know where the program is installed?.

-Ask the user where will he store the data when the program is first run and store that location in the config file. Again, the problem would persist because even before the program could read the config file it would be looking for the "data" folder at the "startup location"

-Use a fixed location for the program and its files... But it does eliminate the flexibility of having it wherever you want... Again, I don't know a lot about Ubuntu and maybe this is the way things are done but surely I would have to fiddle with file permisions and such a lot... I would like an easy installation.

-Figure out a way of telling Ubuntu to run the program "from" its own folder.

So, that's about it for now... Its not actually a BIG issue but I'd really like to solve it.

---

