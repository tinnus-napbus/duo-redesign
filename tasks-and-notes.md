## homepage

The docs.urbit.org homepage should drop you directly into docs view with the
sidebar etc, rather than having the differently styled overview of
developers.urbit.org. The homepage will just be an overview of the system,
explanation of how to navigate the docs, and information about learning
material / courses.

---

## navbar

The navbar will be:

`Language Userspace System Tools Courses Manual Glossary`

Clicking on one of these should take you to the overview of that section
defined in its `_index.md` file.

---

## folders in sidebar

### Design

The left sidebar should be able to render folders as either expandable
subdirectories or a "flat" view where the title is a header and then its
contents are listed below at the same level (see images below). When something
is an expandable folder it should be obvious - with the current design you
can't really tell.

Whether something is flat or expandable should be determined by a field in the
toml at the top of its `_index.md`. Additionally, it should be possible to
specify whether an expandable folder defaults to open or collapsed.

#### flat

![](https://m.tinnus-napbus.xyz/pub/duo/2023-08-01_01h37m14s.png)

#### expandable

![](https://m.tinnus-napbus.xyz/pub/duo/2023-08-01_01h37m32s.png)

---

## section index in sidebar

Currently it's not possible to navigate to a section's `_index.md` file from
the sidebar. This results in us having a separate overview document. We want to
integrate the overviews into the `_index.md` rather than having to maintain two
files. Therefore, it should be possible to click on the flat-mode header
(described above) to go to its index. It should also be possible to get there
in collapsible mode, though this obviously creates a conflict between
click-to-expand and click-to-go-to-index. Hopefully there's a design/dev
solution to this?

---

## navbar in docs

currently the `Langauge Userspace System ...` navbar is not displayed when
you're actually in the docs, you have to go back to the developers.urbit.org
homepage to see it. This makes switching between "root" sections annoying. The
navbar should always be displayed.

---

## glossary

We want a specially designed glossary page, rather than the current glossary
being a boatload of individual pages listed in the sidebar [(see
here)](https://developers.urbit.org/reference/glossary). It should have
something like the following structure:

```
[search bar that live-filters entries as you type]
A B C D E F G H ...

A

Agent
Ames
API
Aqua
...

B

Battery
Behn
Bowl
Bridge
...
```

When you click on a particular entry, it should open it on the same page to
show the content. Maybe a slide-down thingy or just a collapsable thing? A
modal would probably be annoying but I guess that could also work.

Idk if it's possible to pull in the separate `.md` pages for the entries into
one page, whether we need to collect them into one page, or whether they should
be some kind of formally structure thing that can be more easily read
programatically. We want to use these entries for word-definition modals on
other pages too (see below) so maybe a formal datastructure is necessary.

---

## click-for-definition

We want to be able to make words in other docs clickable, and when you click it
shows a modal with the contents of its glossary entry. It is desirable for this
behaviour to be explicitly set in the markdown rather than just automatically
word-matched, as we'd have issues with words used in different contexts
incorrectly showing irrelevant glossary entries when clicked.

We'll there need some kind of syntax to use in markdown docs to make a word
clickable for its glossary definition.

---

## search

search is currently very bad and should be fixed.

## header links

Headers in markdown docs should show a button to copy a link to that section
when hovered, like how github does it, eg:

![](https://m.tinnus-napbus.xyz/pub/duo/2023-08-01_02h01m11s.png)

---

## callout style

foundation-design-system currently has a `{% callout %}` component thingy, but
its styling is very close to codeblocks. It should be distinctly styled so it's
clear it's a callout rather than codeblock when it just contains some text.

---

## codeblock re-collapse

foundation-design-system currently has the ability to make codeblocks default
to collapsed with `{% mode=collapse %}` or something like that. Once
uncollapsed, however, you can't re-collapse it. There should be a way to do
that.

---

## app cards

We want a component aded to foundation-design-system or w/e to create cards for
Urbit apps. The ecosystem section of urbit.org has nicely styled applications
but these are defined in the toml of individual pages [(see here for an
example)](https://raw.githubusercontent.com/urbit/urbit.org/master/content/applications/~bacwyl-samweg/templeochess.md)
which is not ideal. We want a way to add app cards anywhere to a docs markdown
file, and have it render [something like how it does at the top
here](https://urbit.org/applications/~lomder-librun/ballot) except in a nice
little discrete box/card thing. The details we'll need are the the same as in
the toml linked about, just not in the toml but in a `{% app %}`
foundation-design-system custom component or something.

 The details we'll need are the the same as in the toml linked about, just not
 in the toml but in a `{% app %}` foundation-design-system custom component or
 something.

---

## group cards

Same as the above app cards, except for groups. We just need group image, group
name, description and shortcode copy button.

---

## last edited

If possible, it would be good to display the last time the page you're viewing
was edited at the bottom. The current site has this but it seems to display the
time of the last commit for the whole developers site, rather than for
individual pages.

---

## video embeds

We want to be able to easily embed youtube vids or vids we host ourselves on
media.urbit.org

---

## image redesigns

a number of diagrams need to be redesigned with a consistent style. [See
`images.md` for the list](./images.md)

---
