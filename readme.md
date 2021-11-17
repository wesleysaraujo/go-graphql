## Go Lang GraphQL

Exemple de API GraphQL para cadastro e consulta de:

* Categories
* Courses
* Chapters

Esse exemplo utiliza o módulo (gqlgen)[https://gqlgen.com/] para gerar o scaffold com seus devidos modelos

### Implementação dos principais métodos
Os principais métodos responsáveis pelas consultas e mutations estão implementados em:
`graph/schema.resolvers.go`

### Rodar o servidor GraphQL (Playground)
`go run ./server.go`

### Mutations
`mutation createCategory {
  createCategory(input: {
    name: "Linux",
    description: "Cursos de Linux"
  }) {
    id
    name
    description
  }
}

mutation createCourse {
  createCourse(input: {
    name: "Linux para Desenvolvedores",
    description: "Cursos de Ubuntu Linux para desenvolvedores"
    categoryId: "T5577006791947779410"
  }) {
    id
    name
    description
  }
}

mutation createChapter {
  createChapter(input: {
    name: "Primeiros Passos",
    courseId: "T8674665223082153551"
  }) {
    id
    name
  }
}`

### Query
`query findCategories {
  categories {
    id
    name
    description
    courses {
      name
    }
  }
}

query findCourses {
  courses {
    id
    name
    description
    category {
      id
      name
    },
    chapters {
      id
      namehttps://gqlgen.com/
    }
  }
}

query findChapters {
  chapters {
    id
    name
    course {
      name
    }
  }
}
`

