---
title: "How do launchers work?"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by ecs_pf5 on 2007-06-13
I made a launcher on my Desktop and in the 'command' textbox in the launcher setup dialog, tried many variations on

```

gnome-terminal --command "gcc source.c -o executable"
gnome-terminal -e "gcc source.c -o executable"
gnome-terminal --command "gcc /home/user/Desktop/source.c -o executable"

etc etc

```

but, although once or twice it briefly flashed up a terminal, it never managed to run gcc and put an output file on the Desktop.

Am I just getting the syntax slightly wrong or am I fundamentally misunderstanding how launchers work. I know I'm approaching this from the Windows idea of a shortcut or cmd batch file.

Note that my question is more concerned with launchers / links / scripting than gcc, I used gcc as an example, it just happens to be what I'm playing with ATM. (In this case I was trying to make a Desktop link that would compile a C source file to an executable file on the Desktop, with one click.)

---

### Post by jimcooncat on 2007-06-13
Some observations here:

Are you sure "executable" didn't wind up in your /home/*user* directory? That's the directory the launcher runs in, not the /home/*user*/Desktop directory. If so, try specifying a full path before your "executable" file.

~ (the tilda) is an alias for /home/*user*, no matter which user you are.

You could switch to the Desktop directory first, and start your command with *cd ~/Desktop && * which would change your directory then run the rest of your command.

Launchers have a "Application in Terminal" option, so you don't have to use the gnome-terminal command to start with.

You may want to redirect stderr to another file so you can see errors that gcc provides. (Find out more about redirection in the bash documentation.)

---

### Post by mlentink on 2007-06-13
Launchers are a bit like shortcuts in windows. 
You can use a shortcut in windows to launch a batch file (which in Linux would be called a shell script), but in your example, that is not what you did. 
In such a case, you have to combine those commands into a shell script (type them up in an editor, save them with a .sh extension en make them executable). Then you could have typed e.g.  example.sh  as a command in your launcher.

Usually, you would use a launcher to do what their name implies: to launch an application

Does this help?

---

### Post by ecs_pf5 on 2007-06-13
ok |I tried doing it as a .sh script, and pointing a launcher to that. It worked.

then I just tried

```

gcc /home/user/Desktop/source.c -o /home/user/Desktop/executable

```

directly in a launcher. It worked.

I must have missed out that particular syntax combination.. Thanks :)

---

