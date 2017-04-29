# tag-based notes

## Description

Multi-user system that should allow `notes` to be created, edited, deleted and searched by tags and by time of creation. Where `notes` are documents of any predefined kind (markdown, HTML, image, etc.). Each note has one or more assigned tags. The system should implement server-client architecture comunicating via HTTP API. Clients, besides implementing interface to create, to edit, to delete and to view the notes, should implement interface to search by creation time and by tags with realtime hints as well. The realtime hints should show all tags which are `actual` for the provided search query. Where the `actual` means that if one of the suggested tags is chosen, then there is at least one note comply with provided search query. At the moment when no query was provided yet — all available tags are `actual`.

For example, suppose there are documents:

| id   | tags |
| ---: | :--- |
| 0    | picture, fruits, apple, mango |
| 1    | picture, fruits, orange       |
| 2    | picture, animals, rabbit      |
| 3    | picture, animals, cow         |

then for the `provided search queries` the suggestions must be:

| provided search query | suggested tags (hints)        | notes comply with the suggestions |
| :-------------------- | :---------------------------- | :-------------------------------- |
| fruits                | apple, mango, orange, picture | 0, 1                              |
| fruits, apple         | mango, picture                | 0                                 |
| animals, picture      | cow, rabbit                   | 2, 3                              |

A note of one user may be viewed and searched by another user (either registered, or unregisterd), only if special tag `_public` is assigned to the note.

Search can be applied to notes of one user at a time. There should be possibility to enhance the search in such way, that it could be performed for small groups of users.

## Architecture considerations


