---
title: "log into a text console?"
date: 2006-03-30
forum: Absolute Beginner Talk
---

### Post by danr on 2006-03-30
Could someone please tell me how to **log into a text console**.

Thank you, Dan

---

### Post by dcstar on 2006-03-30
[QUOTE=danr]Could someone please tell me how to **log into a text console**.

Thank you, Dan[/QUOTE]
If you mean once you are already in a X session, CTRL-ALT-F1 will get you a text  terminal that you use the exact same username and password to log in to.

---

### Post by danr on 2006-03-30
I tried to do what you said, it asks for my login and I type my user name, then it asks for my password but it doesn't do anything on the screen when I try to enter it. None of the keys do anything and then login times out.

Thanks, Dan

---

### Post by IYY on 2006-03-30
It's not supposed to give you any feedback until you press return (that is 'Enter' in newspeak). Just type in your password, press return and you'll be logged in.

---

### Post by danr on 2006-03-30
That’s what I do, I entered my user name and then hit enter, it takes my user name and then it wants my password but it will not let me enter anything at all. None of the keys will affect the cursor, it will not enter a character of any kind.
My password is all numbers, I tried with the numeral lock off or on, I treid the numbers along the top of the keyboard and they will not work either, any key letter or number.

What’s going on, I tried restarting it a couple of times and it does the same thing every time.
It says, “after 60 seconds, login timed out” or words to that effect

Thanks again for your help, Dan

---

### Post by tikal26 on 2006-03-30
Maybe if you tell us exactly what you are doing we could help? 
I am wondering Why do you want to log in to a text console?

---

### Post by danr on 2006-03-30
I was trying to follow the instructions at this site for my scanner.
I wanted to see if "sane" is pre-installed or not.


[http://www.gjaeger.de/scanner/misc/howtos/InstallationsanweisungEn/node6.html](http://www.gjaeger.de/scanner/misc/howtos/InstallationsanweisungEn/node6.html)

I dont know why it will not let me enter my password after taking my user name. 

I'm trying to learn about Linux Ubuntu, and I not off to a very good start!

Thanks, Dan

---

### Post by tikal26 on 2006-03-30
danr:
you don't need to do that to check if sane is preinstall just go to synaptic if using ubuntu
adept if using kubuntu
and type sane
it would tell you if its install or not
just click on install and you are done

If for some reason you do not get it it is probably because you don't have the universe repos enable.
Ubuntu
open synaptic (I think that it is under system)
settings
repositories
New and you should fill it in like the screenshot I posted

I know that at the beginning it can be frustrating because its different, but if you hang in there we can probably help you trough the problems. Once you learn how linux works you will understand it's advantages.

If you use kubuntu and need directions let me know

---

### Post by engla on 2006-03-30
[QUOTE=danr]That’s what I do, I entered my user name and then hit enter, it takes my user name and then it wants my password but it will not let me enter anything at all. None of the keys will affect the cursor, it will not enter a character of any kind.
My password is all numbers, I tried with the numeral lock off or on, I treid the numbers along the top of the keyboard and they will not work either, any key letter or number.

What’s going on, I tried restarting it a couple of times and it does the same thing every time.
It says, “after 60 seconds, login timed out” or words to that effect

Thanks again for your help, Dan[/QUOTE]
This is the misunderstanding; as said way above, just type in the pass and hit enter: **nothing is supposed to show up**, this is how the terminal password prompts are designed. So blindly type the password and hit enter.

Yeah, and you don't have to go ctrl-alt-F1 to get a terminal, you can open Applications > Accessories > Terminal to get a small one in a window (in the normal GNOME desktop).

---

### Post by danr on 2006-03-30
Ok that worked, not quite the same as you said and I don’t know why yet but it did list “sane”when I entered the name in “search” on the page you said to go to.

That’s enough for today I have to hit the rack, but I will be back again for more help!

I think (hope) your right about it getting easier in time, today’s basically my first day so I guess I see what happens.

I’d like to leave one more question in closing for the night, and please answer it at your leisure as I wont see any responses until tomorrow after work.

Why couldn’t I enter my password, or anything at all when the computer asked for it after accepting my user name.   

Good night all!

Many thanks, Dan

---

### Post by uzi09 on 2006-03-31
lol, no offense or anything, but i don't know if you're joking or not so just to be on the safe side, i'll assume you aren't (once again, no offense).

you may have heard that linux/unix are a LOT more secure than Windows. one place where this shows up is when you are typing passwords in. what linux and unix do is hide the password. Windows hides it too, but you can still see how many characters a password is because it just replaces the character with a *. in unix/linux - it is a lot more secure because it won't even show a * when you type something in **THE SYSTEM IS STILL GETTING YOUR CHARACTERS, BUT JUST DOESN'T DISPLAY IT ON THE SCREEN** so no one around you can find out how many characters your password is and try to guess it.

so even though you are typing something (and you can hit backspace a ton of times too if you think you mistyped something to erase it all and start again) and nothing shows on the screen doesn't always mean that the OS is not getting the info.

:D cheers
uzi

---

### Post by danr on 2006-03-31
Hey, no offense taken! Thanks for the response, I see what you mean, if I would have just typed my password without looking at the screen it would have let me in.

That’s exactly what was happening, I’d start to enter it and I’d notice it was not moving or entering the * to cover my entry and then I’d stop typing, duh!

Well I learn something new every day. 

My own password kept _me_ out too!

Thanks again, Dan

---

### Post by christhemonkey on 2006-03-31
i used to get really confused as to why it never showed asterisks (*) when i typed my password in terminal, but you get used to it evenentually, honest!

---

