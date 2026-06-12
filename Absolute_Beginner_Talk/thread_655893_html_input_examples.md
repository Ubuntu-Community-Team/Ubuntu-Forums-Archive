---
title: "html input examples"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by larry Gaminde on 2008-01-01
I am trying to write something In HTML code  I thought would be simple but I have no Idea where to start. I want it to be something like this

button----------- then some text  --------------  and a count
button----------- then some text  --------------  and a count
button----------- then some text  --------------  and a count



like a voting machine you can select only one button at a time and the count will add one count per vote

button    -----               larry        -----                18
button    -----              mary        -----                 15
button    -----               bob         -----                 6

so if I click on the button for bob and then hit (send) (one more button) then the 6 will now be 7 until someone else or that same person votes again. only one persons count will update per vote

---

### Post by bwtranch on 2008-01-01
There are a lot of great tutorials on the web and some great free HTML programs in Add/Remove. Depending on your expertise. There are some blog writing programs that make you look like a whiz, without writing any code at all. Google around, and I'm sure you'll find just what you need.

---

### Post by mouseboyx on 2008-01-01
This has to have a server backend to record this such as php but if you wanted the bones:
Did you want this to be like a poll that everyone could see or like a client side app that would be different for everyone if they changed it?
```

<form method="post" action="serversideproccessor.php"><input name="1" value="Button" type="submit"></form> Text 1
```

---

### Post by mouseboyx on 2008-01-01
pollhost.com

---

### Post by bump_ on 2008-01-01
I think doing it in just HTML gets pretty advanced. If you used a scripting language such as php or javascript, the task will will be made simpler.

---

### Post by larry Gaminde on 2008-01-02
Thanks everyone it looks like this might be over my head at this time so I will look at Pollhost and see if this works looks like it will be quick and easy just hope that the people logging in will be able to see the numbers updating

Thanks

---

