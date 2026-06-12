---
title: "Help with paths"
date: 2006-12-05
forum: Absolute Beginner Talk
---

### Post by coolbun2 on 2006-12-05
I have an application that is on the WEB which displays several Flash video files which are also on the same server as the application. This runs fine on my edgy box. For bandwidth reasons, I want to place these Flash videos on my local box which is running edgy. However, when I did this, the video will not load. I have a user account called user007 and the files were placed in /home/user007/video/. This is the path that is specified on the application on the WEB followed by the actual name of the video file. I've set permissions to that folder to (777) and still no luck. 
I think there is something with the security or permissions for an external application trying to access local files.
Anyone have a solution for this?

---

### Post by Arisna on 2006-12-05
What are the permissions on the video files themselves?

---

### Post by coolbun2 on 2006-12-05
the same - 777. I've even done this for the hierarchy as well

---

### Post by Arisna on 2006-12-05
You set the entire hierarchy to 777?  As in, the root folder ("/") on the system?  That would allow any user to do anything to any file--hence, it isn't a good idea.  For the folder and these video files, 755 would be enough to eliminate permission problems and maintain security.

OK, now I'm starting to see what the issue is.  Even though you have the same files and folder on the local machine, the web server will still pull the files from itself, because the web page is stored there.  You would have to save the web page locally for this to work.

---

### Post by coolbun2 on 2006-12-05
Thanks, and I just the permissions up to the user level and not root.

Anyways this works fine on a Windows box so I'm thinking that it has to do with linux architecture. For the windows box, I specified the application to look for the flv files in c:/my_vids/ and it works fine. If it can work on Windows without having the web page stored locally, I figure it can work on Linux but cannot figure out why its not.

---

### Post by scc4fun on 2006-12-05
> **coolbun2 said:**
> Thanks, and I just the permissions up to the user level and not root.

Anyways this works fine on a Windows box so I'm thinking that it has to do with linux architecture. For the windows box, I specified the application to look for the flv files in c:/my_vids/ and it works fine. If it can work on Windows without having the web page stored locally, I figure it can work on Linux but cannot figure out why its not.
It may be that the application is made to work only with windows paths. Without knowing what web app it is, I can't say anything further.

---

### Post by coolbun2 on 2006-12-05
Its a Flash/php app on a Linux server(Centos). The app takes the path that you type as a string, so it should not be limited to Windows paths.

Ok I just tried another same type of situation.
I put a basic html page on the web that has one image. If I place that image locally on the linux box and change the path on the web page to look for it locally (/home/user007/helloworld.jpg),it doesn't display.

Any ideas?

---

### Post by Voxxi on 2006-12-05
Try putting the file in the same folder as the application itself and then just typing the filename (With no paths).

For instance, if the application was in /var/www, just stick the file in there and enter the filename (helloworld.jpg).

---

### Post by coolbun2 on 2006-12-05
Ok, I figured it out!!! - Nothing to do with linux - my bad.

Its Firefox's security. It prevents local file access whereas IE on Windows obviously doesn't.

Here is a tutorial for the work-around with an extension you can install.

http://kb.mozillazine.org/Links_to_local_pages_don't_work

---

