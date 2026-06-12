---
title: "Setting up user document folders"
date: 2006-06-30
forum: Absolute Beginner Talk
---

### Post by Rich3077 on 2006-06-30
Okay so now my hard drive is looking messy due to all the downloading I have been doing, so its time to organize and tidy up a bit. 

I was all set and ready to setup user documents folders simular to what is used under Windows.. for example
/Rich's Documents/Rich's Music
Then I stopped myself because I realized that the file folder names are not exactly user freindly when it comes to typing them in the terminal. 
Also I would like to know if there is any reason that I shouldnt use spaces 
in the folder name? I noticed that I cannot find other folders on the system with spaces so it got me wondering.
Any tricks or tips for setting up user folders? 
Damn I feel lame asking such a question.. talk about being a tottal newb! 
:oops: 


Peace
Rich

---

### Post by Rich3077 on 2006-06-30
Okay now I dont feel so silly for asking. I logged out to run to the corner store and when I came back I got an error.. something about my home folder and permissions. I did make a folder in there.

Edit, error= User's $Home/.dmrc file is being ignored

Peace
Rich

---

### Post by xtacocorex on 2006-06-30
I don't know about the error, but here is a list of my /home directory and what each directory means for me.

[LIST]
[*]aerospace 
[INDENT]- My general aerospace files[/INDENT]
[*]backups    
[INDENT]- Backups[/INDENT]
[*]bin           
[INDENT]- My personal bin for my executables[/INDENT]
[*]boinc        
[INDENT]- Stuff for BOINC[/INDENT]
[*]cfd          
[INDENT] - Started directory for CFD Projects[/INDENT]
[*]Desktop     
[INDENT]- The General Ubuntu Desktop directory[/INDENT]
[*]music        
[INDENT]- My Music[/INDENT]
[*]personal    
[INDENT]- Personal files[/INDENT]
[*]pictures     
[INDENT]- My Pictures[/INDENT]
[*]projects     
[INDENT]- Coding Projects[/INDENT]
[*]school        
[INDENT]- All of my School Files[/INDENT]
[*]src            
[INDENT]- General source directory for 1 file FORTRAN codes[/INDENT]
[*]tuxmag       
[INDENT]- Holds all my issues of Tux Magazine[/INDENT]
[*]utility         
[INDENT]- Holds all the downloaded .tar.gz, .deb files[/INDENT]
[*]videos        
[INDENT]- My Videos[/INDENT]
[*]workspace   
[INDENT]- This is autocreated from Eclipse (Java IDE)[/INDENT]
[/LIST]

---

### Post by gr0kzer0 on 2006-06-30
If you want to create a directory with spaces in its name, you use the \ character as an "escape" character.  So the command

```
mkdir big\ documents
```

would create a directory called "big documents".

---

### Post by IYY on 2006-06-30
There's nothing wrong with spaces in filenames, but terminal users prefer short, lowercase, single word names. It's laziness, really. ;-) 

Anyway, to access a folder with a space in the terminal:

```
cd "My Documents"
```

or

```
cd My\ Documents
```

or, the best way:

```
cd My
```

Then press the 'tab' key and have the shell auto-complete your request.

---

