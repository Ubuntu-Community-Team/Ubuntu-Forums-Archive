---
title: "how to create and use functions in php"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by arathi on 2007-07-16
Hi 
I want to create function in php to retrieve record from the database.The record should be retrieved whenever function is called.Plz help me how to  create and call  function in php.

---

### Post by AngelBreath on 2007-07-16
Actually you have to post is in another place. Try "Programming Talk" in ubuntu forums. I think you ll have faster and more accurate answers.

---

### Post by Dr Small on 2007-07-16
[php]
function getdb()
     {
$sqlhost = 'localhost';
$sqluser = 'root';
$sqlpass = '';
$db = 'phpadminpanel';
$tableprefix = 'pap_'

## CONNECT TO DATABASE ##
$connect = mysql_connect($sqlhost, $sqluser, $sqlpass)
or die( "Could not connect to SQL server" );

mysql_select_db($db, $connect)
or die ("Could not open database:" .mysql_error() );


## RETRIEVE NOTES FROM DATABASE ##

$selectstatement = mysql_query("SELECT * FROM {$tableprefix}notes ORDER BY `notes`");

while($info = mysql_fetch_array($selectstatement))
{
echo $info['notes'];
}

    }

[/php]

---

