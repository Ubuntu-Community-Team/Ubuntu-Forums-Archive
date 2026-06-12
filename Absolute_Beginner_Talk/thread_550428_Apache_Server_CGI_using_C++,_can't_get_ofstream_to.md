---
title: "Apache Server: CGI using C++, can't get ofstream to co-operate"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by jjaeger4 on 2007-09-13
Ok, I looked around here a little but couldn't find anything in particular to get my problem. What I want to do, basically, is get my C++ program to work to take the information a person enters on a form on my web page to go into a file (working as a database or something to that affect. Here is about what I've got for the program.

```
#include <iostream>
#include <fstream>
using namespace std;

int main()
{
        char a[256];
        cout << "Content-type: text/html\n\n";
        cout << "<h1>Hello in C++</h1>\n";
        cout << "<pre>\n";

        cin >> a;
        cout << a;
        ofstream file("./myFile");
        file << a;
        file.close();

        cout << "</pre>\n";
}

```

That is the code for the C++ part of the cgi.

This is the code for the form on the web page.

```
<center><form action = "a.cgi" method = post>
<label>Enter your name:</label>
<input size = "20, 20" name = "name" maxstring = "20">
<button type = "submit" name = "choice" value = "1">Yes</button>
<button type = "submit" name = "choice" value = "2">No</button> 
<button type = "submit" name = "choice" value = "3">Maybe</button>
</form></center>

```

It won't write anything to the "myFile" I'm not sure what I need to do... I've not worked with CGI too much but I've got intermediate experience in C++. I can work it in Python too if that makes any difference? Kthnx!

- Jesse

---

### Post by bwhitaker on 2007-09-14
Does the web user www-data have write access to the file?

```

sudo touch myFile
sudo chown www-data:www-data myFile
sudo chmod 644 myFile

```

---

