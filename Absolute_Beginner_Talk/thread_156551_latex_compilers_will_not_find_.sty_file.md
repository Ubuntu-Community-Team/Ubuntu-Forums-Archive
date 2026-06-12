---
title: "latex compilers will not find .sty file"
date: 2006-04-07
forum: Absolute Beginner Talk
---

### Post by aerowrestlerisu on 2006-04-07
Hi, I am having a serious problem with my latex. I need to use a lot of .sty files from my university, but the compilers...namely kile won't find them. I have used the texhash command but that doesn't solve the problem.....Does anyone know how to fix it?

---

### Post by neoflight on 2006-04-09
[QUOTE=aerowrestlerisu]Hi, I am having a serious problem with my latex. I need to use a lot of .sty files from my university, but the compilers...namely kile won't find them. I have used the texhash command but that doesn't solve the problem.....Does anyone know how to fix it?[/QUOTE]

where did u put the sty files...
actually kile is not the one to find them...its the latex thats needed sty files...

did u have root privilages while running texhash....carefully look at the output of that command....

---

### Post by kolesarm on 2006-05-03
[QUOTE=aerowrestlerisu]Hi, I am having a serious problem with my latex. I need to use a lot of .sty files from my university, but the compilers...

if you have superuser priviliges, you need first to put them in the correct directory, ie ```
/usr/local/share/texmf/
```, perhaps create a subdirectory for your own files, eg  ```
/usr/local/share/texmf/tex/latex/
```

namely kile won't find them. I have used the texhash command but that doesn't solve the problem.....Does anyone know how to fix it?[/QUOTE]

run```
sudo texhash
```

---

### Post by nanotube on 2006-05-03
easiest way to use your custom .sty files is to put a copy into the same directory as your latex project. that way it will surely find your .sty. of course, that means that every project you want to create using that .sty will have to have a copy of it in its directory - but oh well, at least it will work.

---

### Post by harishg on 2006-05-03
do they offer the files as .dtx and .ins files.If they do it then you can just extract the relevant files to /usr/local/share/texmf/latex.If not another way to do is just save the files in the folder and while defining the file give the link to the directory its stored.

For eg. say your files are stored in a dir called StyleFiles just use 
\usepackage{StyleFiles/watermark} and similarly for all.

---

### Post by darckhart on 2006-05-03
somewhat related, i run into problems using that texhash command. when i'm in the dir, and i run 'texhash', it spits out all that stuff and of course, doesnt have permission to write in some directories sometimes. so i try 'sudo texhash' but then bash comes back and tells me it can't find a sudo texhash command. what gives? (i ended up switching up to root to do it, but i dont think i should have to....)

---

### Post by xtacocorex on 2006-05-03
I had this same problem, probably for the same report aerowrestlerisu.

I fixed it by editing the /etc/texmf/texmf.cnf file as root and uncommenting and changing this line:

% User texmf trees can be catered for like this...
HOMETEXMF = $HOME/school/texmf

with the location of the ISU Aero templates in your home dir.

Running sudo texhash didn't work for me the multiple times I ran it.

---

### Post by thk on 2006-05-03
You can also add the path to the TEXINPUTS environment variable.

---

### Post by lodp on 2006-10-18
sorry for digging up this old thread, but the title just matched my problem so well..

when i compile documents in kile using additional packages, latex tells me that it can't find those packages. i did a search of "texmf" on my system, copied the .sty files to every single of the folders that were found (like /usr/share/texmf for example), and ran "sudo texhash". didn't change anything.

i also created a texmf folder with the .sty files in it in /home/me -- and edited /etc/texmf/texmf.cnf to the following:

> % User texmf trees can be catered for like this...
HOMETEXMF = $HOME/texmf

but no success, even though a file called ls-R is created there when i run texhash, and it contains the names of the sty files.

i remember i had this working beautifully on breezy. the only thing that DOES work is putting the .sty files in the folder where the .tex document is... i know it's stupid, but that_just_doesn't_feel_right :)

i de-installed tetex and am now downloading the texlive2005 image, and will install it along with the latest version of kile (from sources).

i would appreciate any pointers...

---

### Post by izak on 2008-02-12
Aha! This is an old thread but I struggled with the exact same problem and have found the solution so hopefully anybode googleing will find this:)

The problem is that when you copy your directory with your new classes etc. into /usr/share/texmf-tetex/<location> and use a command like sudo cp the files are copied as having root only privelages! After running sudo texhash latex knows where to find them but does not have permission to read them!

Kile hides this from you since it only outputs the error message "cannot find <your class>.cls" But if you look at the latex ouput tab you can see that it tried to access the cls file but had "permission denied". 

So after copying the files and running sudo texhash be sure to use sudo chmod to make all the files readable by normal users.

Hope this helps somebody out there!

---

