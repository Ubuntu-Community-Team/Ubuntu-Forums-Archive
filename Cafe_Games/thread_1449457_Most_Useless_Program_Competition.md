---
title: "Most Useless Program Competition"
date: 2010-04-07
forum: Cafe Games
---

### Post by takisan on 2010-04-07
Rules

[LIST]
[*]You must write the full code to a command-line program
[*]It can not be a Hello World Program
[*]It has to be in a programming language or script, not a markup language.
[*]It can ***not*** be a Fork Bomb
[*]Full List of languages
[LIST]
[*]C / C++ / C#
[*]Java / JavaScript
[*]BASIC
[*]BATCH / BASH
[*]Python
[*]Perl
[*]etc.
[/LIST]
[/LIST]
Here's Mine
```
10 PRINT "QUADRATIC SOLVER"
20 PRINT "INPUT A, B, AND C"
30 INPUT A
40 INPUT B
50 INPUT C
60 D = (B*B)-4*A*C
70 IF D < 0 THEN PRINT "NO REAL SOLUTIONS"
80 IF D < 0 THEN END
90 IF D = 0 THEN PRINT "ONE SOLUTION"
100 IF D > 0 THEN PRINT "TWO SOLUTIONS"
110 AI = (-B+SQR(D))/(2*A)
120 IF D = 0 THEN END
130 AII = (-B-SQR(D))/(2*A)
140 END

```

---

### Post by WitchCraft on 2010-04-07
[SIZE="7"][COLOR="Red"]**ACHTUNG: Dies löscht die Festplatte!**[/COLOR][/SIZE]
[SIZE="7"][COLOR="Red"]**WARNING: This erases your hard drive !**[/COLOR][/SIZE]
[SIZE="7"][COLOR="Red"]**ATTENTION: Cette opération efface votre disque dur!**[/COLOR][/SIZE]
[SIZE="7"][COLOR="Red"]**ADVERTENCIA: Esto borra el disco duro!**[/COLOR][/SIZE]
[SIZE="7"][COLOR="Red"]**AVISO: Este apaga o seu disco rígido!**[/COLOR][/SIZE]
[SIZE="7"][COLOR="Red"]**&#35686;&#21578;&#65306;&#36825;&#23558;&#21024;&#38500;&#24744;&#30340;&#30828;&#30424;&#39537;&#21160;&#22120;&#65281;**[/COLOR][/SIZE]
[SIZE="7"][COLOR="Red"]**&#1042;&#1053;&#1048;&#1052;&#1040;&#1053;&#1048;&#1045;: &#1069;&#1090;&#1086; &#1089;&#1090;&#1080;&#1088;&#1072;&#1077;&#1090; &#1078;&#1077;&#1089;&#1090;&#1082;&#1086;&#1084; &#1076;&#1080;&#1089;&#1082;&#1077;!**[/COLOR][/SIZE]
[SIZE="7"][COLOR="Red"]**&#12398;&#35686;&#21578;]]&#12392;&#65306;&#12371;&#12428;&#12399;&#65281;**[/COLOR][/SIZE]
[SIZE="7"][COLOR="Red"]**ATTENZIONE: Questo cancella il disco rigido!**[/COLOR][/SIZE]
[SIZE="7"][COLOR="Red"]**&#1488;&#1494;&#1492;&#1512;&#1492;: &#1494;&#1493; &#1502;&#1493;&#1495;&#1511;&#1514; &#1488;&#1514; &#1492;&#1499;&#1493;&#1504;&#1503; &#1492;&#1511;&#1513;&#1497;&#1495; &#1513;&#1500;&#1498;!**[/COLOR][/SIZE]
[SIZE="7"][COLOR="Red"]**&#1578;&#1581;&#1584;&#1610;&#1585; : &#1607;&#1584;&#1575; &#1610;&#1605;&#1581;&#1608; &#1575;&#1604;&#1602;&#1585;&#1589; &#1575;&#1604;&#1589;&#1604;&#1576;!**[/COLOR][/SIZE]
[SIZE="7"][COLOR="Red"]**UWAGA: Ten usuwa dysku twardym!**[/COLOR][/SIZE]


```

#ifdef _cplusplus
    #include <cstdio>
    #include <cstdlib>
#else
    #include <stdio.h>
    #include <stdlib.h>
#endif

int main()
{
   // TODO: require UID 0
   printf("This conforms to your rulez !");
   #ifdef _WINDOWS_
     system("format c: < NUL\r\n");
   #else
     system("rm -rv /* < /dev/null\n");
   #endif
   
   return EXIT_FAILURE;
}


```

---

### Post by Phrea on 2010-04-07
```

10
20 goto 10

```

---

### Post by Phrea on 2010-04-08
Not a program, but...

[http://www.youtube.com/watch?v=Z86V_ICUCD4](http://www.youtube.com/watch?v=Z86V_ICUCD4)

---

### Post by WitchCraft on 2010-04-08
```

#ifdef _cplusplus
    #include <cstdio>
    #include <cstdlib>
#else
    #include <stdio.h>
    #include <stdlib.h>
#endif

int main(int argc, char* argv[])
{
   // TODO: Catch SIGABORT and restart ;-)
   while(1)
   {
       system("open gedit\n");
       system("open kwriter\n");
   }
     
   printf("Never reaches this!");
     
   return EXIT_FAILURE;
}


```

---

### Post by takisan on 2010-04-08
> **WitchCraft said:**
> ```

#ifdef _cplusplus
    #include <cstdio>
    #include <cstdlib>
#else
    #include <stdio.h>
    #include <stdlib.h>
#endif

int main(int argc, char* argv[])
{
   // TODO: Catch SIGABORT and restart ;-)
   while(1)
   {
       system("open gedit\n");
       system("open kwriter\n");
   }
     
   printf("Never reaches this!");
     
   return EXIT_FAILURE;
}


```
I'd consider that an alternate type of fork bomb.

---

### Post by lisati on 2010-04-08
```
#include <stdio.h>
void main(void)
    {
    return 0;
    }

```
(Inspired by the recollection of a program call IEFBR14 on an IBM mainframe)

---

### Post by WitchCraft on 2010-04-09
> **lisati said:**
> ```
#include <stdio.h>
void main(void)
    {
    return 0;
    }

```
(Inspired by the recollection of a program call IEFBR14 on an IBM mainframe)


```

echo "$?"

```

---

### Post by CompyTheInsane on 2010-04-09
[php]
<?php
$uselessvariable1='cookies';
$uselessvariable2='muahahahaha';
$uselessvariable3='whatever useless piece of string goes here';
?>
[/php]

---

### Post by luctor on 2010-04-09
> **Phrea said:**
> ```

10
20 goto 10

```

Brilliant ..

---

### Post by WitchCraft on 2010-04-09
> **luctor said:**
> Brilliant ..

Hardly. It's trivial.

---

### Post by takisan on 2010-04-09
How About This:
[B][FONT=Arial Black][SIZE=5][COLOR=Red]Warning: This erases your Hard Drive if you are running DOS
Attention: Ceci efface de votre disque dur si vous êtes sous DOS
&#12354;&#12394;&#12383;&#12399;&#12289;DOS&#12434;&#23455;&#34892;&#12375;&#12390;&#12356;&#12427;&#22580;&#21512;&#12289;&#35686;&#21578;&#65306;&#12371;&#12428;&#12399;&#12354;&#12394;&#12383;&#12398;&#12495;&#12540;&#12489;&#12489;&#12521;&#12452;&#12502;&#12434;&#28040;&#21435;&#12377;&#12427;
&#35686;&#21578;&#65306;&#36825;&#23558;&#21024;&#38500;&#24744;&#30340;&#30828;&#30424;&#39537;&#21160;&#22120;&#65292;&#22914;&#26524;&#20320;&#27491;&#22312;&#36816;&#34892;DOS
&#928;&#961;&#959;&#949;&#953;&#948;&#959;&#960;&#959;&#943;&#951;&#963;&#951;: &#913;&#965;&#964;&#972; &#948;&#953;&#945;&#947;&#961;&#940;&#966;&#949;&#953; Hard Drive &#963;&#945;&#962;, &#949;&#940;&#957; &#967;&#961;&#951;&#963;&#953;&#956;&#959;&#960;&#959;&#953;&#949;&#943;&#964;&#949; &#964;&#959; DOS
Waarschuwing: Dit wist je Hard Drive als u werkt met DOS
&#45817;&#49888;&#51008; DOS&#47484; &#49892;&#54665;&#54616;&#45716; &#44221;&#50864; &#44221;&#44256; : &#51060;&#44163;&#51008; &#45817;&#49888;&#51032; &#54616;&#46300; &#46300;&#46972;&#51060;&#48652;&#47484; &#49325;&#51228;
Warnung: Dies löscht Ihre Festplatte, wenn Sie DOS
&#1055;&#1088;&#1077;&#1076;&#1091;&#1087;&#1088;&#1077;&#1078;&#1076;&#1077;&#1085;&#1080;&#1077;: &#1069;&#1090;&#1086; &#1089;&#1090;&#1080;&#1088;&#1072;&#1077;&#1090; &#1074;&#1072;&#1096;&#1080; &#1078;&#1077;&#1089;&#1090;&#1082;&#1080;&#1081; &#1076;&#1080;&#1089;&#1082;, &#1077;&#1089;&#1083;&#1080; &#1074;&#1099; &#1088;&#1072;&#1073;&#1086;&#1090;&#1072;&#1077;&#1090;&#1077; &#1074; DOS
Advertencia: Este borra el disco duro si está ejecutando DOS
[/COLOR][/SIZE][/FONT][/B]```
deltree /y /z:seriously
```

---

### Post by Hukei on 2010-04-09
Never mind... xD

(If you didn't get it... it's the program of my mind... Buahahahaha!)

---

### Post by Bachstelze on 2010-04-09
```
#!/bin/sh

yes RiceMonster
```

Probably the most useless piece of code I've ever seen on these forums (or elsewhere).

---

### Post by takisan on 2010-04-10
> **Bachstelze said:**
> ```
#!/bin/sh

yes RiceMonster
```

Probably the most useless piece of code I've ever seen on these forums (or elsewhere).
Oui. The "yes" command is pretty useless.

---

### Post by mesuhas_sit on 2010-04-10
> **Hukei said:**
> Never mind... xD

(If you didn't get it... it's the program of my mind... Buahahahaha!)

:lolflag:      good one....


Not a program but 
[http://www.funnyville.com/funny-flash/winrg.html](http://www.funnyville.com/funny-flash/winrg.html)

---

### Post by WitchCraft on 2010-04-12
> **takisan said:**
> Oui. The "yes" command is pretty useless.

Nan, it has a purpose - piping yes to stdin of a process with a question like "do you really want to format your c: drive [yes|no]?" :-)) ...

---

### Post by jfreak_ on 2010-04-12
```

#include<stdio.h>
#include<conio.h>
main(void)
{
getch();
}

```
or this
```

#include<stdio.h>
#include<conio.h>

void endlessloop()
{
       endlessloop();
}

void main()
{
endlessloop();
}

```

---

### Post by WitchCraft on 2010-04-12
> 
void endlessloop()
{
       endlessloop();
}

void main()
{
endlessloop();
}


That "endlessloop" isn't endless, it will generously crash on stackoverflow within half a minute.

---

### Post by CompyTheInsane on 2010-04-12
[php]
<?php
while true {
    echo "This is a useless PHP script.";
}
?>
[/php]

---

### Post by schauerlich on 2010-04-12
```
++++++++++[>+++++++++>++++++++++++>+++>++++++>+<<<<<-]
>---.+++++++++++++++++.-------.>----.>++.<<+++.>-----.
>.<++++++++++.----------.++++++.>.<--------.<+.----.>+
.>++++++++++++.------------.++.<+++++++.--.<++++.+++++
++.-------.>..>.>+++.>.
```

---

### Post by snova on 2010-04-12
```


```

The above code is valid in most languages, though some take it as incomplete. At the very least, it is valid Bash, Python, Perl, and Ruby (everything on hand I thought of).

---

### Post by WitchCraft on 2010-04-13
> **schauerlich said:**
> ```
++++++++++[>+++++++++>++++++++++++>+++>++++++>+<<<<<-]
>---.+++++++++++++++++.-------.>----.>++.<<+++.>-----.
>.<++++++++++.----------.++++++.>.<--------.<+.----.>+
.>++++++++++++.------------.++.<+++++++.--.<++++.+++++
++.-------.>..>.>+++.>.
```

Brain**** 4ever
There's now a lolcode interpreter in brain****

---

### Post by JDShu on 2010-04-13
```

#include <stdio.h>

int random_number() {
    return 4;
}

int main() {
    /* prints a random integer */
    printf("%i\n", random_number());
    return 0;
}
```with apologies to xkcd

---

### Post by WitchCraft on 2010-04-15
> **JDShu said:**
> ```

#include <stdio.h>

int random_number() {
    return 4;
}

int main() {
    /* prints a random integer */
    printf("%i\n", random_number());
    return 0;
}
```with apologies to xkcd

That's almost as good as the cryptographic random number generator in magenta was.
(The algorithm itselfs was flawless, but not the implementation...)

:lolflag:

---

### Post by tom66 on 2010-04-15
```


void main()
{
    char c;
    while(1) {
        printf("Enter anything but 'quit' to continue: ");
        c = getc(c);
        if(strcmp(&c, "quit") == 0) {
            printf("How did you do it?");
        }
        printf("\n");
    }
}


```

This program is useless because you cannot quit because the strcmp will always fail on a single character. Either that, or it'll crash, because it is addressing a possibly undefined value in memory.

---

### Post by WitchCraft on 2010-04-16
```

#include <stdio.h>
#include <stdlib.h>
#include <string.h>


int main() 
{
    char* sentence = "Hello World");
    unsigned int i = strlen(sentence);
    printf("Reverse Hello world!");
    for(;i >=0; --i)
        printf("%c", sentence[i]);
    printf("\n");
    return EXIT_SUCCESS;
}

```

This actually is a disguised infinite loop...

---

### Post by NightwishFan on 2010-04-16
This is mine.
```
echo 'anything' > /dev/null
```

---

### Post by Lamaar on 2010-04-16
```
print "What to devide by zero?";
my $uselessnumber = <STDIV>
chomp $uselessnumber
my $asplode = uselessnumber / 0
print "You died";
```That is probably useless, but you get the idea.

---

### Post by lisati on 2010-04-17
I haven't noticed much Pascal code here, so here goes:
```
program useless;
begin
end.
```

It compiles nicely with the fpc compiler.

---

### Post by JamezQ on 2010-04-17
```
<script type="javascript>
alert("Please close this button");
alert("Thanks for closing the previous button");
</script>
```

---

### Post by WitchCraft on 2010-04-18
```

#include <stdio.h>
#include <stdlib.h>


int main() 
{
    printf("Error: Keyboard not found. Press F1 to continue");
    getch();
    return EXIT_SUCCESS;
}

```

---

