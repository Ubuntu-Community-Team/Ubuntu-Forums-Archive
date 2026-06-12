---
title: "Where do I permantly modify PATH?"
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by Mr. Angry Pants on 2007-01-31
Hi all,
I'm still sort of giggling at reading my "Dear Mr. Angry Pants, Welcome to the Ubuntu Forums!" email I got from the mods.  Anyway...  I have looked everywhere I can think of on the Internet and in this forum and I can't find the answer.  Perhaps I just don't know where or how to look properly, but that's why I'm posting here in the beginner forums.  All I'm trying to do is to add a directory in my home directory (e.g. /home/user/application) to the PATH so that regardless of what pwd I am in, any program in that directory will run.

Everywhere I look tells me to look into .bashrc and .bash_profile.  Man pages in ubuntu tell me to look in the .bash_profile, .bash_login and .profile and /etc/profile files.  None of these files contain the string which is the actual PATH.  I can temporarily add the directory to the PATH by either manually typing "PATH=/blah/blahblah/blahblahlbhalhbalhba:/blah/blahblah/blahblah" or trying to append it to the end of that, but I don't know how to make it stick.  Once I reboot the machine and type "env" to check out the path (or # echo $PATH), it's all gone.  I swear I've given it the old college try to figure it out on my own, but I'm just stumped.  Can anyone please help me figure out how to permanently modify my path variable (actually, I'm not even sure if that's the correct terminology, but it seems like that's what it should be called).

Thanks in advance.

M.A.P.

---

### Post by ComplexNumber on 2007-01-31
> **Mr. Angry Pants said:**
> Hi all,
I'm still sort of giggling at reading my "Dear Mr. Angry Pants, Welcome to the Ubuntu Forums!" email I got from the mods.  Anyway...  I have looked everywhere I can think of on the Internet and in this forum and I can't find the answer.  Perhaps I just don't know where or how to look properly, but that's why I'm posting here in the beginner forums.  All I'm trying to do is to add a directory in my home directory (e.g. /home/user/application) to the PATH so that regardless of what pwd I am in, any program in that directory will run.

Everywhere I look tells me to look into .bashrc and .bash_profile.  Man pages in ubuntu tell me to look in the .bash_profile, .bash_login and .profile and /etc/profile files.  None of these files contain the string which is the actual PATH.  I can temporarily add the directory to the PATH by either manually typing "PATH=/blah/blahblah/blahblahlbhalhbalhba:/blah/blahblah/blahblah" or trying to append it to the end of that, but I don't know how to make it stick.  Once I reboot the machine and type "env" to check out the path (or # echo $PATH), it's all gone.  I swear I've given it the old college try to figure it out on my own, but I'm just stumped.  Can anyone please help me figure out how to permanently modify my path variable (actually, I'm not even sure if that's the correct terminology, but it seems like that's what it should be called).

Thanks in advance.

M.A.P.
as an expample, if you wanted to add /usr/local/MyProgs/bin to your PATH, just add the following to the end of your  .bash_profile file in your home directory:
  "export PATH=$PATH:/usr/local/MyProgs/bin" (without the quotes)


the important point is that you need to place "export" before when you set the path variable.

---

### Post by Mr. Angry Pants on 2007-01-31
Ah... it's just that easy.  So it has to export every single time.  Exactly the answer I was looking for, thank you!!!!

<ponder>I wonder where the default path that comes with bash is kept, then...</ponder>

Thanks again for the answer I needed.  I can now sleep tonight :)

---

### Post by Mr. Angry Pants on 2007-01-31
Just as an FYI, I had to modify the .bashrc file instead of the .bash_profile file in my home directory.  I'm using Dapper Drake (6.06) release, if it makes a difference.  It works now.  Thanks again.

---

### Post by xzatech on 2008-06-17
hello all but similiar ? I know to export in the .bashrc
}but at the moment my echo $PATH is displaying a /home/johndoe/bin and that bin part does not exist

}i want to delete it or modify it how can i modify to keep what there needs to be there in place globaly so no user path are set up wrong as well

---

