---
title: "open .doc using wine ---how??"
date: 2006-03-10
forum: Absolute Beginner Talk
---

### Post by animesh on 2006-03-10
added winword.exe to applications in wine but how to use it to open a  .doc file?

---

### Post by ariek on 2006-03-10
Why use MSoffice when there is OpenOffice?

---

### Post by Kimm on 2006-03-10
you could write a script and put it in /usr/bin then assosiate .doc files with the script.

do this:

sudo gedit /usr/bin/winword

Put this in gedit and save:

> 
#!/bin/bash
cd <path to folder containing winword.exe>*
wine winword.exe @$


Then do:

sudo chmod +x /usr/bin/winword

Then right click on a .doc file and do preferences to assosiate with winword

But as ariek pointed out.. why use MS office when you have openOffice.org?

[i]*PS:
I'm guessing that <path to folder containing winword.exe> should be:
/home/<username>/.wine/drive_c/Program\ Files/Microsoft\ Office/Office10[/i]

---

### Post by rboss on 2006-03-10
You really might want to install OpenOffice.org or Abiword. They offer much more comfort than winword.

---

### Post by Kimm on 2006-03-10
no offence, but he asked for a sulotion to how to open .doc files using winword not for uss to recommend other apps. If you acctually provide an answer to his question it is OK to recommend him using something else.

---

### Post by trorion on 2006-03-10
[QUOTE=Kimm]no offence, but he asked for a sulotion to how to open .doc files using winword not for uss to recommend other apps. If you acctually provide an answer to his question it is OK to recommend him using something else.[/QUOTE]
/signed
And thank you for your answer Kimm, I won't be using winword but your answer told me how to do it for other things.

---

### Post by Kimm on 2006-03-10
**EDIT: Bugg fixed, updated!**

hmm... after some though, that doesnt work at all!
I worked some on it... and as I dont know bash scripting very well I wrote a little help program in C++

first off, download and install this:
[http://i.domaindlx.com/MrKimm/win-soft_2.0b_i386.deb](http://i.domaindlx.com/MrKimm/win-soft_2.0b_i386.deb)
Alternate link:
[http://www.proupload.com/uploads/1142173905.deb](http://www.proupload.com/uploads/1142173905.deb)

(if the link doesnt work or you are on ppc/amd64 see bottom)

then change the script (/usr/bin/winword) to:

```

#!/bin/bash
win-soft "<path to winword.exe>" "$@"

```

Now, if the link at the top didnt work, or you are using and amd64/ppc computer, copy these sources to gedit and save them as win-soft.cc:

```

#include <iostream>
#include <string.h>
#include <stdlib.h>

char *drives[26] = {"a:","b:","c:","d:","e:","f:","g:","h:","i:","j:","k:","l:","m:","n:","o:","p:","q:","r:","s:","t:","u:","v:","w:","x:","y:","z:"};

int drive_detect();

int main(int argc, char *argv[])
{
	int x, x_ = 0;
	char temp[200];
	char runme[350];
	
	if(argc < 2)
	{
		std::cout<<"To few arguments...\nSynthax:\n\n";
		std::cout<<"win-soft <exe file> <exe arguments>\n\nExiting!";
		return 0;
	}
	
	x = drive_detect();
	system("clear");
	
	std::cout<<"The '/' wine drive is: \""<<drives[x]<<"\"\n";
	
	strcpy(temp, argv[2]);
	x_ = strlen(temp);
	
	while(x_ >= 0)
	{
		std::cout<<temp[x_];
		if(temp[x_] == '/')
			temp[x_] = '\\';
			
		x_--;
	}
	
	std::cout<<"\n"<<temp<<"\n";
	
	strcpy(runme, "wine \"");
	strcat(runme, argv[1]);
	strcat(runme, "\" \"");
	strcat(runme, drives[x]);
	strcat(runme, temp);
	strcat(runme, "\"");
	
	std::cout<<runme<<"\n";
	
	system(runme);
	
return 0;
}

int drive_detect()
{
	int x = 0, x_;
	char test[50];
	
	while(x <= 26)
	{
		strcpy(test, "~/.wine/dosdevices/");
		strcat(test, drives[x]);
		strcat(test, "/usr/bin/link");
		
		x_ = system(test);
		
		if(x_ == 256)
			return x;
			
		x++;
	}
	
return 0;
}

```

now open a terminal and type:

g++ win-soft.cc -o win-soft
sudo mv win-soft /usr/bin/win-soft

That should set you up :)

[i]PS.
the synthax for win-soft is: win-soft <path to exe-file> <exe-file argument>
for use with other software (tested with foobar2000)[/i]

---

### Post by aysiu on 2006-03-10
[QUOTE=Kimm]no offence, but he asked for a sulotion to how to open .doc files using winword not for uss to recommend other apps. If you acctually provide an answer to his question it is OK to recommend him using something else.[/QUOTE] No offense, but people posting in the Absolute Beginner section don't always know that they don't need Microsoft Word to open .doc files.

If the post had begun, "I know I can open .doc files with OpenOffice, but I prefer to use Word," then it would make sense not to offer, "Have you tried OpenOffice?"

To the OP, is there something special you need Microsoft Word for that OpenOffice can't handle?

---

### Post by Kimm on 2006-03-10
aysiu, ok, perhaps I was exagerating somewhat. I did not take into acount what forum this is.

to the rest, bugg fixed! my above post has been updated!

---

