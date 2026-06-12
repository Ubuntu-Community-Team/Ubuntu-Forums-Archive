---
title: "beginner php question"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by woodsonoversoul on 2007-05-31
*I posted this to "Programing talk" but wasn't getting many responses. Thought someone might know here*

Alright what about this, I´m getting an unable to connect message with the code:

// set database server access variables:
$host = "localhost";
$user = "dan";
$pass = "mypass";
$db = "testdb";

// open connection
$connection = mysql_connect($host, $user, $pass) or die ("Unable to connect!");

when I´ve just created the database. I´m using my root name and password. I didn´t set up any user privliges so I assumed access would be granted under root, is this incorrect or is there a problem with my code?

---

### Post by bobplano on 2007-05-31
never mind i didn't read it right

why don't you replace unable to connect with mysql_error()

---

