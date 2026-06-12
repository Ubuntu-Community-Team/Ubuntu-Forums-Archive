---
title: "Latex - Table Numbering"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by NanakiXIII on 2008-01-14
I created a table and created a reference to it like this:

```

~\ref{table:const}

\begin{table}[h]  \label{table:const} 
...
\caption{...}
\end{table}

```

This is the only table I have in my document, and the caption shows "Table 1", but the reference for some reason returns "3" instead of "1". Does anyone have any idea why that might be happening?

---

### Post by mali2297 on 2008-01-14
> **NanakiXIII said:**
> I created a table and created a reference to it like this:

```

~\ref{table:const}

\begin{table}[h]  \label{table:const} 
...
\caption{...}
\end{table}

```

This is the only table I have in my document, and the caption shows "Table 1", but the reference for some reason returns "3" instead of "1". Does anyone have any idea why that might be happening?

Try moving the label next to the caption instead, like this
```

\begin{table}[h]
...
\caption{...}\label{table:const} 
\end{table}

```

---

### Post by NanakiXIII on 2008-01-14
That produces the same affect, I'm afraid.

By the way, I do have other references, but they are to images and all of them (both before and after the table) are numbered normally. I don't suppose those other references might affect things?

---

### Post by mali2297 on 2008-01-14
Well, that's strange. Have you run latex twice to get the references right? (One is often told to do so.)

---

### Post by NanakiXIII on 2008-01-14
I've run Latex numerous times because when I could not find the solution to this problem, I simply continued with the rest of my document.

Perhaps it is noteworthy that the references have been sketchy ever since I started this document. Sometimes they will suddenly only show up as ??, though I have changed nothing about them. Then removing or adding that ~ in the reference will sometimes fix it (I'm sure that's considered bad practice, but I have to try something). I haven't been able to detect any patterns in this behavior.

---

### Post by NanakiXIII on 2008-01-14
Well, this is indeed strange. I have changed nothing about my references and have only worked on other parts of my document, but all my references are shown normally now. I have no idea what is going on, I'm keeping my fingers crossed that the problem does not return.

Thank you for your replies so far, mali. Though, if anyone does know what is happening to my document, I'm still very much interested to hear it.

---

### Post by sjov on 2008-05-25
> **NanakiXIII said:**
> I created a table and created a reference to it like this:

```

~\ref{table:const}

\begin{table}[h]  \label{table:const} 
...
\caption{...}
\end{table}

```

This is the only table I have in my document, and the caption shows "Table 1", but the reference for some reason returns "3" instead of "1". Does anyone have any idea why that might be happening?


Try putting the caption before the label, that ought to do it.

---

### Post by chrisby on 2008-06-24
none, of the suggestions here helped me with the same problem.  I did find this [http://en.wikibooks.org/wiki/LaTeX/Labels_and_Cross-referencing#Fixing_wrong_labels]("http://en.wikibooks.org/wiki/LaTeX/Labels_and_Cross-referencing#Fixing_wrong_labels")

Which suggested embedding the label within the caption like:
\caption{Close-up of a gull \label{fig:gull} }

Using this method worked perfectly.  I am so happy, I can concentrate on writing again!\\:D/\\:D/\\:D/

---

