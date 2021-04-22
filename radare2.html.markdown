---
category: tool
tool: radare2
contributors:
    - ["pancake", "https://github.com/trufae"]
filename: LearnRadare2.txt
---


[Radare2](http://www.radare.org)

Radare2 is a framework and toolchain for reverse engineering, exploiting,
forensics and any other

Best way to learn r2 is ... you 

You can watch r2con talks or read the book


## Basic concepts

* Everything is a file
* commands are 1 letter
* visual, panels, graphs



## First steps

```
    vim <filename>   # Open <filename> in vim
    :help <topic>    # Open up built-in help docs about <topic> if any exists
    :q               # Quit vim
    :w               # Save current file
    :wq              # Save file and quit vim
    ZZ               # Save file and quit vim
    :q!              # Quit vim without saving file
                     # ! *forces* :q to execute, hence quiting vim without saving
    ZQ               # Quit vim without saving file
    :x               # Save file and quit vim, shorter version of :wq

    u                # Undo
    CTRL+R           # Redo

    h                # Move left one character
    j                # Move down one line
    k                # Move up one line
    l                # Move right one character

    Ctrl+B 	         # Move back one full screen
    Ctrl+F 	         # Move forward one full screen
    Ctrl+D 	         # Move forward 1/2 a screen
    Ctrl+U           # Move back 1/2 a screen

    # Moving within the line

    0                # Move to beginning of line
    $                # Move to end of line
    ^                # Move to first non-blank character in line

    # Searching in the text

    /word            # Highlights all occurrences of word after cursor
    ?word            # Highlights all occurrences of word before cursor
    n                # Moves cursor to next occurrence of word after search
    N                # Moves cursor to previous occerence of word

    :%s/foo/bar/g    # Change 'foo' to 'bar' on every line in the file
    :s/foo/bar/g     # Change 'foo' to 'bar' on the current line
    :%s/\n/\r/g      # Replace new line characters with new line characters

    # Jumping to characters

    f<character>     # Jump forward and land on <character>
    t<character>     # Jump forward and land right before <character>

    # For example,
    f<               # Jump forward and land on <
    t<               # Jump forward and land right before <

    # Moving by word

    w                # Move forward by one word
    b                # Move back by one word
    e                # Move to end of current word

    # Other characters for moving around

    gg               # Go to the top of the file
    G                # Go to the bottom of the file
    :NUM             # Go to line number NUM (NUM is any number)
    H                # Move to the top of the screen
    M                # Move to the middle of the screen
    L                # Move to the bottom of the screen
```

## Customization

* radare2rc
* changing theme
* tuning asm.vars

## Help docs:

Vim has built in help documentation that can accessed with `:help <topic>`.
For example `:help navigation` will pull up documentation about how to navigate
your workspace!

`:help` can also be used without an option. This will bring up a default help dialog
that aims to make getting started with vim more approachable!

## Modes:

Vim is based on the concept on **modes**.

- Command Mode - vim starts up in this mode, used to navigate and write commands
- Insert Mode  - used to make changes in your file
- Visual Mode  - used to highlight text and do operations to them
- Ex Mode      - used to drop down to the bottom with the ':' prompt to enter commands

```
    i                # Puts vim into insert mode, before the cursor position
    a                # Puts vim into insert mode, after the cursor position
    v                # Puts vim into visual mode
    :                # Puts vim into ex mode
    <esc>            # 'Escapes' from whichever mode you're in, into Command mode

    # Copying and pasting text

    y                # Yank whatever is selected
    yy               # Yank the current line
    d                # Delete whatever is selected
    dd               # Delete the current line
    p                # Paste the copied text after the current cursor position
    P                # Paste the copied text before the current cursor position
    x                # Deleting character under current cursor position
```

## The 'Grammar' of vim

Vim can be thought of as a set of commands in a
'Verb-Modifier-Noun' format, where:

- Verb     - your action
- Modifier - how you're doing your action
- Noun     - the object on which your action acts on

A few important examples of 'Verbs', 'Modifiers', and 'Nouns':

```
    # 'Verbs'

    d                # Delete
    c                # Change
    y                # Yank (copy)
    v                # Visually select

    # 'Modifiers'

    i                # Inside
    a                # Around
    NUM              # Number (NUM is any number)
    f                # Searches for something and lands on it
    t                # Searches for something and stops before it
    /                # Finds a string from cursor onwards
    ?                # Finds a string before cursor

    # 'Nouns'

    w                # Word
    s                # Sentence
    p                # Paragraph
    b                # Block

    # Sample 'sentences' or commands

    d2w              # Delete 2 words
    cis              # Change inside sentence
    yip              # Yank inside paragraph (copy the para you're in)
    ct<              # Change to open bracket
                     # Change the text from where you are to the next open bracket
    d$               # Delete till end of line
```

## Scripting

The easiest way to script r2 is by using r2pipe. This protocol is can be
used from almost any language (shellscript, C, V, Java, Rust, Go, Perl
and even Python!).

```python
import r2pipe

r2 = r2pipe.open('/bin/ls')
print(r2.cmd('?e Hello World'))
r2.quit()
```

* sync vs async
* inside r2 vs spawn

## Bindings

* r2api
* r2pipe-api
* r2libr

## Some shortcuts and tricks

TODO

### References

[Radare2 | Home](http://www.radare.org/)

