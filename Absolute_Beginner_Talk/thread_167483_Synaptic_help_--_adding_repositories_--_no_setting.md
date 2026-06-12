---
title: "Synaptic help -- adding repositories -- no settings button"
date: 2006-04-28
forum: Absolute Beginner Talk
---

### Post by sqlplus on 2006-04-28
I'm sure this is so simple I've got to be missing something here...

I'm trying to follow the instructions here to add the universe and mulitverse repositories -- [https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

However, when I open Synaptic and go to Settings -> Repositories, there is no Settings button in the dialog to allow me to check "show disabled software sources". Has Synaptic changed very recently and if so how do I add new repositories?

Thanks...

---

### Post by jazzmuzik on 2006-04-28
It's a little confusing, but there are TWO "settings" selections. The instructions say so. I think you missed it. Try this:

System, Administration, Synaptic Package Manger, Settings, Repositories, Settings.

---

### Post by sqlplus on 2006-04-28
Yes, that was how I understood the instructions. However, for me, there is no settings button in that last dialog window.  If you tell me how to take a screenshot of the window I can try to post an image  :)

---

### Post by sqlplus on 2006-04-28
I forgot to mention that I am using Dapper beta...

---

### Post by pbaehr on 2006-04-28
I noticed that too when I was following along with a tutorial. It's a bit different in Dapper. I believe you can just skip that step.

---

### Post by mostwanted on 2006-04-28
[http://monkeyblog.org/ubuntu/installing.html#enabling_extra_repositories](http://monkeyblog.org/ubuntu/installing.html#enabling_extra_repositories)

That says it all in plain text and images (guide created on Dapper).

---

### Post by jazzmuzik on 2006-04-28
You can edit the repository list from the command line:

Open the Terminal program and you get a command prompt.

Enter:

gksudo gedit /etc/apt/sources.list

Now you can add and edit the repositories. URL's beginning with # are disabled. Remove the # and save the file to enable them.

---

