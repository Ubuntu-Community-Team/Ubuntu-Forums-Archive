---
title: "Jinzora tweaks and configuration"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by kasperbs on 2007-10-07
Hi If anyone in here are familiar with jinzora I would be glad if you could help me a bit. The Jinzora forums are not very widely used and the explanations in there are not very concise.

1st Problem: What is the connection between MPD and jinzora library
I read everywhere that I need to update the MPD database to match jinzora, but how do I do that and why is that? And can this be automated with cron maybe?

2nd Problem: Weblinks, how to
> I just added a new feature to MPD- the ability to use weblinks instead of local paths within MPD. Set it like this:
$jbArr[0]['prefix'] = 'http';
This is the only info you get from the jinzora website. Which file should I look at and where should I make these changes?

3rd. Problem: Monitoring of library
Can jinzora monitor my music library so that when I make changes it will also be so in Jinzora? I have tried to at album artwork to some of my albums (both in the tag and as a folder.jpg) but none of them shows up. Not even when doing rescan media. I have to delete the folder, then rescan, then import the folder again with the art in it and then rescan again.

4th. Problem: Meta data retrieval issue
This issue was first raised on the jinzora forums nearly a year ago, and haven't had a single reply despite people reporting in the thread the have same isuues.
When i retrieve meta data from the internet I get this error message:
> PHP Warning:  stristr() [function.stristr]: Empty delimiter. in /home2/geekleek/public_html/jinzora/frontend/display.php on line 189
These are the lines in display.php
```
$d = @dir($include_path . "temp/cache");
if ($d !== false) {
while ($entry = $d->read()) {
if (stristr($entry,$name)){
@unlink($include_path."temp/cache/". $entry);

```
Does anyone know what that could mean?

5th Problem: Browse problem when adding Media
When trying to add media vi Admin Main > System Tools > Media Manager I get the following error when pushing the browse button:
> The requested URL /jinzora2/install.xml/browse.php was not found on this server.

If you could just answer some of the questions I would be happy - The thing is Im kinda stuck and any pointers would be nice.

---

