---
title: "Boinc on ubuntu 64 bit"
date: 2006-10-25
forum: Absolute Beginner Talk
---

### Post by RicktheBrick on 2006-10-25
I have been trying to attach a project to Boinc for the last 3 days.  I decided to try ./run_manager so I opened a terminal and changed directories to BOINC.  I than ran the run_manager and to my surprise it opened the boinc manager and did attach itself to a project which it started.  So I decided to close the terminal afterwhich the boinc manager also shut down.  I than went to applications and restarted the boinc manager.  It did not have any projects and refused to start any as before.  If I again go to the terminal program and again use ./run_manager it will start the boinc manager and the project will be there and will run as long as I have the terminal program running.  How can I automate this?  I know in windows I could start an editor and type in the commands and than save it as a bat file which I could put in the autostart folder and expect it to execture at boot time.

---

### Post by dbd on 2006-10-25
In linux you can make a script to run programs in a similar way as a bat file can. Then you can set up that script to run on start up.

To do this create a text file, lets call it boinc.sh. Now edit the file so that it contains the complete location of your boinc manager that you want to run, and then after that put the '&' sign, this will mean that the script will not wait for boinc to finish before exiting, but will just start boinc then close. For example the file may say:
> /somewhere/somewherelese/run_manager &
then change the scripts permissions so it can be executed, do this by using the command:
> chmod +x boinc.sh

Now if you are using kubuntu move the script to ~/.kde/Autostart/ and you are done.

If you are using ubuntu then I'm now sure where you should move it to, but you can set it to run on startup by going to to System->Preferences->Sessions, click the "Startup Programs" tab, click the "Add" button, and using the dialog that pops up browse to the script we just corrected.
[HTML][/HTML]
Now it should start everytime you start X.

Good luck, let us know if you have any problems.


Oh, and be sure to join BOINC team ubuntu, see my sig for a link :)

---

### Post by Doctor J on 2006-11-03
@RicktheBrick:

What project are you trying to attach to?  The project has to supply its "cruncher" software for each platform.  In my case, failure to attach to Rosetta@Home was caused by their failure to provide an AMD64 client.  The solution is to trick BOINC into supplying "anonymous" as the platform, rather than "AMD64" cf. [http://boinc.berkeley.edu/anonymous_platform.php](http://boinc.berkeley.edu/anonymous_platform.php) [see "Project-specific applications" halfway down the page].

---

