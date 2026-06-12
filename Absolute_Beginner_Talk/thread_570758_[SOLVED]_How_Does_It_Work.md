---
title: "[SOLVED] How Does It Work?"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by snkiz on 2007-10-08
How Does Ubuntu Reconize Diffrent File Types And What To Do With Them? Is There A Config File Some Where? I Ask Because My Ubuntu Isn't Doing This Anymore.

---

### Post by Thingymebob on 2007-10-08
You can right click any file, select properties, then the open with tab, and choose what you want ubuntu to do with it. This selection will apply for all files of the same type

---

### Post by snkiz on 2007-10-08
Funny Thing I Tried That And Nothing Happened

---

### Post by snkiz on 2007-10-08
There Must Be A Database Somewhere. Everything Was Fine, Then One Day I Boot Up And I Have Default Icons All Over And Ubuntu Doesn't Know What To Do With The Files Anymore.

---

### Post by llamakc on 2007-10-08
The easiest way to answer your question (without getting too detailed) is for you to give us a single example. What file were you trying to open up, and when doing so what did you EXPECT it to do?

---

### Post by rsambuca on 2007-10-08
It sounds like your MIME database is borked somehow.  Try re-installing 

gnome-mime-data
desktop-file-utils
mime-support
shared-mime-info

---

### Post by snkiz on 2007-10-08
Three Examples Off The Top Of My Head (not @ My Compter Now, Gotta Love Opra Mini) Launchers On My Desktop Have .desktop Appended To Them, They Read As Text Files.  Images Files And Archive Files (all Types) Say No Known Progam For This File Type Is Says Is Appication/octlet Stream. They All Worked Before And I Promise I Havn't Touched A System File In Weeks.

---

### Post by llamakc on 2007-10-08
When you get back to the computer create a new user. Login as THAT user and see if all is well. If it is, you have something screwy in your /home/USER directory, like conf files or such. You may not REMEMBER having done anything, but that doesn't mean you haven't just forgotten.

This happens often around here when folks are trying new how-to's and begin cut/pasting into the terminal. Usually it's a permission issue.

---

### Post by Rui Pais on 2007-10-08
> **snkiz said:**
> There Must Be A Database Somewhere. Everything Was Fine, Then One Day I Boot Up And I Have Default Icons All Over And Ubuntu Doesn't Know What To Do With The Files Anymore.

Well usually MIME types database is located, generically for all users, at /etc/mailcap.

I doubt that this would be of any use to you... Just check if that file exist. If not, reinstall mime-support (it's created by that package installation).

To update your mime types run:
```
sudo update-mime
```

hth


PS it must be as tiresome to you write all words started with uppercase as we to read them ;)

---

### Post by snkiz on 2007-10-08
My Net Is Down At The Moment So Downloading Is Not An Option. I Did Try To Install A Theme From My Home Folder Golbaly As Root. (didn't Work Btw) I Know Those Files Have My Permisions And Not Root But As I Said Not System Files.

---

### Post by llamakc on 2007-10-08
/etc/mime.types

---

### Post by snkiz on 2007-10-08
Sorry Bout The Caps Flaw In My Phone Can't Shut It Off. Thanks All For Telling Me Where The File Is. Usally If I Can Find And Read The Config Im Looking For I Can Fix It, At Least So Far. Its Amazing How Much I've Learned About Linux In Just 5 Months Messing Up Ubuntu. I Saw A Signature Here That Said `if It Aint Broke You Didn't Learn Anything` How True.

---

### Post by snkiz on 2007-10-20
I Found The Answer! And I Think I Know The Cause. I Moved Some Files From My Home Directory Into /usr/share/<folder> Nothing Critical, Just Images, Icons, I Was Trying To Make A Theme From My Home Folder Avaible System Wide. Btw Havn't Figured That Out Yet I Think You Have To Make A .deb To Do It. Anyway I Didn't Change The File Permisions *WARNING linux NEVER Handles This Well Most Of My Problems Have Stemed From This* So When I Rebooted It Caused An Error In Nautilus That Made It Not Reconize Some File Types, Even though All The Files The Helpfull People Here Told Me To Look At Appeared Normal. After Learning A Bit More About Mime Types. I Discoverd The Command To Reset Thing Was Update-mime-database But When You Enter That Comand It Asks For A Path To The Database Witch I Found At /usr/share/mime So To Summerize First Fix Any Permision Issues You May Have The Enter The Comand Update-mime-database /usr/share/mime And Volia A Painful Lession Learned. Cheers!

---

