---
title: "Cant Launch anything!!!!"
date: 2006-08-09
forum: Absolute Beginner Talk
---

### Post by galego on 2006-08-09
Ok well is not totally true; i just cant figure out how to get launcher to work. 
this is what i want to do:

GrubEd---- shortcut.
        needs to be run with sudo (it wont run otherwise)

in the launcher command line i put the path (actualy i found if i dont know the path i can just drag the file over to the line and it puts the complete path in for me; no typing needed) the problem is with the sudo part, if i put it in front of the path nothing happens, if i leave it out i get "sudo" error, if put "sudo sh GrubEd.sh" in "do this first" i get nothing. 

any comments or tips would be great!!

---

### Post by MrHorus on 2006-08-09
If it's a graphical programme you have to launch it with gksudo rather than sudo AFAIK.

---

### Post by Tomosaur on 2006-08-09
Uh yeah sorry about that. Did you select the launcher to run in a terminal? If not, either do that, or change 'sudo' to 'gksudo'. Alternatively, open up a terminal and CD to the GrubEd directory, then try 'sudo sh GrubEd.sh'.

---

### Post by galego on 2006-08-09
[I]Uh yeah sorry about that. Did you select the launcher to run in a terminal? If not, either do that, or change 'sudo' to 'gksudo'. Alternatively, open up a terminal and CD to the GrubEd directory, then try 'sudo sh GrubEd.sh'.
[/I]
yeah in terminal no problem and your "little" program works really nice BTW. I just would like to have a lancher as im really lazy like that. i did tick the run in terminal but no go. i will try gksudo.

oh yeah MrHorus, sorry im kinda new at all this forum stuff, what is AFAIK? 

just to double check i dont have to do anything in the "advanced" tab of the launcher GUI correct?

---

### Post by Tomosaur on 2006-08-09
Well, I use a launcher and it works fine for me. I'll paste you the details I have, just edit them to suit you:

Command: gksudo sh /home/tom/GrubEd/GrubEd.sh

If you do it like this, you don't have to have the 'Run in terminal?' option selected. However, if you run from a launcher and the help file is not in the home directory, then the 'help' button won't work properly. You either have to move the help file itself, or alter GrubEd.sh so it points directly to the right location.

The next version will hopefully have resolved these problems, and I'll throw in an example launcher for everyone.

EDIT: And no, you don't have to do anything in the adanced tab :P

---

### Post by galego on 2006-08-09
Nice!!! that helps a ton. my issue was with sudo. so this wil work now. and yeah the help button doesnt reference my file as i misunderstood your posted instructions but i understadn that i have to move that file to the home directory. thnaks again and your program IS really handy.

thank you!!:p

---

### Post by Tomosaur on 2006-08-09
Cheers for the comments :)

---

