# Oficina de código: Desafio Go II

### Objetivo:
A seguir, apresenta-se um desafio integrador que nos permitirá avaliar todos os tópicos abordados no curso.

## Sistema de marcação de consultas
Pretende-se implementar uma API que permita administrar a marcação de consultas para uma clínica odontológica, que deve atender aos requerimentos a seguir:

* ### Administração de dados de dentistas:
  Listar, adicionar, alterar ou excluir dentitas. Registrar seus **sobrenome, nome e matrícula**. Solicita-se o desenvolvimento de um **CRUD** para a entidade **Dentista**.
  #### Métodos
  Requisições para a API devem seguir os padrões:

  | Método   | Descrição                                                    |
  |----------|--------------------------------------------------------------|
  | `POST`   | Adicionar dentista.                                          |
  | `GET`    | Trazer dentista pelo seu ID.                                 |
  | `PUT`    | Atualizar dentista.                                          |
  | `PATCH`  | Atualizar um dentista através de algum dos seus campos.      |
  | `DELETE` | Excluir dentista.                                            |

  ### Request / Responses
  ### Adicionar dentista [POST /api/v1/dentists]
  + Request (application/json)

      + Body

              {
                "surname": "Silva",
                "name": "João",
                "license_number": "00000001"
              }

  + Response 201 (application/json)
      + Body

             {
                 "id": 1,
                 "surname": "Silva",
                 "name": "João",
                 "license_number": "00000001"
             }
  + Response 400 (application/json)
      + Body

             {
                 "code": 400,
                 "status": "error",
                 "message": "invalid data provided",
                 "time_stamp": "2022-12-07 14:55:13"
             }

  ### Buscar dentista [GET /api/v1/dentists/{id}]
  + Request (application/json)
      + Body

              {
                "surname": "Silva",
                "name": "João",
                "license_number": "00000001"
              }
  + Response 200 (application/json)
      + Body

             {
                 "id": 1,
                 "surname": "Silva",
                 "name": "João",
                 "license_number": "00000001"
             }
  + Response 400 (application/json)
      + Body

             {
                 "code": 400,
                 "status": "error",
                 "message": "invalid id provided",
                 "time_stamp": "2022-12-07 14:55:13"
             }
  + Response 404 (application/json)
      + Body

             {
                 "code": 404,
                 "status": "error",
                 "message": "dentist not found",
                 "time_stamp": "2022-12-07 14:55:13"
             }

  ### Atualizar dentista [PUT /api/v1/dentists/{id}]
    + Request (application/json)
        + Body

                {
                  "surname": "Almeida Silva",
                  "name": "João",
                  "license_number": "05000001"
                }
    + Response 200 (application/json)
        + Body

               {
                   "id": 1,
                   "surname": "Almeida Silva",
                   "name": "João",
                   "license_number": "05000001"
               }
    + Response 400 (application/json)
        + Body

               {
                   "code": 400,
                   "status": "error",
                   "message": "invalid id provided",
                   "time_stamp": "2022-12-07 14:55:13"
               }
    + Response 400 (application/json)
        + Body

               {
                   "code": 400,
                   "status": "error",
                   "message": "invalid data provided",
                   "time_stamp": "2022-12-07 14:55:13"
               }
    + Response 404 (application/json)
        + Body

               {
                   "code": 404,
                   "status": "error",
                   "message": "dentist not found",
                   "time_stamp": "2022-12-07 14:55:13"
               }

  ### Atualizar dentista [PATCH /api/v1/dentists/{id}]
    + Request (application/json)
        + Body

                {
                  "surname": "Silva",
                }
    + Response 200 (application/json)
        + Body

               {
                   "id": 1,
                   "surname": "Silva",
                   "name": "João",
                   "license_number": "05000001"
               }
    + Response 400 (application/json)
        + Body

               {
                   "code": 400,
                   "status": "error",
                   "message": "invalid id provided",
                   "time_stamp": "2022-12-07 14:55:13"
               }
    + Response 400 (application/json)
        + Body

               {
                   "code": 400,
                   "status": "error",
                   "message": "invalid data provided",
                   "time_stamp": "2022-12-07 14:55:13"
               }
    + Response 404 (application/json)
        + Body

               {
                   "code": 404,
                   "status": "error",
                   "message": "dentist not found",
                   "time_stamp": "2022-12-07 14:55:13"
               }

  ### Excluir dentista [DELETE /api/v1/dentists/{id}]
    + Request (application/json)

        + Headers

                SECRET_TOKEN: [TOKEN]

    + Response 200 (application/json)
        + Body

               {
                   "success": "dentist deleted"
               }
    + Response 400 (application/json)
        + Body

               {
                   "code": 400,
                   "status": "error",
                   "message": "invalid id provided",
                   "time_stamp": "2022-12-07 14:55:13"
               }
    + Response 404 (application/json)
        + Body

               {
                   "code": 400,
                   "status": "error",
                   "message": "an error occurred while trying to delete dentist, please check if a dentist with ID provided exist or he has not/held appointments",
                   "time_stamp": "2022-12-07 14:55:13"
               }

* ### Administração de dados de pacientes:
  Listar, adicionar, alterar ou excluir pacientes. Registrar seus **sobrenome, RG, nome e matrícula**. Solicita-se o desenvolvimento de um **CRUD** para a entidade **Paciente**.
  #### Métodos
  Requisições para a API devem seguir os padrões:

  | Método   | Descrição                                                    |
  |----------|--------------------------------------------------------------|
  | `POST` | Adicionar paciente.                                            |
  | `GET` | Trazer paciente pelo seu ID.                                    |
  | `PUT` | Atualizar paciente.                                             |
  | `PATCH` | Atualizar um paciente através de algum dos seus campos.       |
  | `DELETE` | Excluir paciente.                                            |

  ### Request / Responses
  ### Adicionar paciente [POST /api/v1/patients]
    + Request (application/json)

        + Body

                {
                  "surname": "Rocha",
                  "name": "Julia",
                  "identity_number": "00000001",
                  "created_at": "07/12/2022",    
                }

    + Response 201 (application/json)
        + Body

               {
                  "id": 1,
                  "surname": "Rocha",
                  "name": "Julia",
                  "identity_number": "00000001",
                  "created_at": "07/12/2022",  
               }
    + Response 400 (application/json)
        + Body

               {
                   "code": 400,
                   "status": "error",
                   "message": "invalid data provided",
                   "time_stamp": "2022-12-07 14:55:13"
               }

  ### Buscar paciente [GET /api/v1/patients/{id}]
    + Request (application/json)
        + Body

    + Response 200 (application/json)
        + Body

               {
                  "id": 1,
                  "surname": "Rocha",
                  "name": "Julia",
                  "identity_number": "00000001",
                  "created_at": "07/12/2022",  
               }
    + Response 400 (application/json)
        + Body

               {
                   "code": 400,
                   "status": "error",
                   "message": "invalid id provided",
                   "time_stamp": "2022-12-07 14:55:13"
               }
    + Response 404 (application/json)
        + Body

               {
                   "code": 404,
                   "status": "error",
                   "message": "patient not found",
                   "time_stamp": "2022-12-07 14:55:13"
               }

  ### Atualizar paciente [PUT /api/v1/patients/{id}]
    + Request (application/json)
        + Body

                {
                  "surname": "Queiroz",
                  "name": "Julia",
                  "identity_number": "00000001",
                  "created_at": "07/12/2022",  
               }
    + Response 200 (application/json)
        + Body

               {
                  "id": 1,
                  "surname": "Queiroz",
                  "name": "Julia",
                  "identity_number": "00000001",
                  "created_at": "07/12/2022",  
               }
    + Response 400 (application/json)
        + Body

               {
                   "code": 400,
                   "status": "error",
                   "message": "invalid id provided",
                   "time_stamp": "2022-12-07 14:55:13"
               }
    + Response 400 (application/json)
        + Body

               {
                   "code": 400,
                   "status": "error",
                   "message": "invalid data provided",
                   "time_stamp": "2022-12-07 14:55:13"
               }
    + Response 404 (application/json)
        + Body

               {
                   "code": 404,
                   "status": "error",
                   "message": "patient not found",
                   "time_stamp": "2022-12-07 14:55:13"
               }

  ### Atualizar paciente [PATCH /api/v1/patients/{id}]
    + Request (application/json)
        + Body

                {
                  "identity_number": "04333330",
                }
    + Response 200 (application/json)
        + Body

               {
                  "id": 1,
                  "surname": "Queiroz",
                  "name": "Julia",
                  "identity_number": "04333330",
                  "created_at": "07/12/2022",
               }
    + Response 400 (application/json)
        + Body

               {
                   "code": 400,
                   "status": "error",
                   "message": "invalid id provided",
                   "time_stamp": "2022-12-07 14:55:13"
               }
    + Response 400 (application/json)
        + Body

               {
                   "code": 400,
                   "status": "error",
                   "message": "invalid data provided",
                   "time_stamp": "2022-12-07 14:55:13"
               }
    + Response 404 (application/json)
        + Body

               {
                   "code": 404,
                   "status": "error",
                   "message": "patient not found",
                   "time_stamp": "2022-12-07 14:55:13"
               }

  ### Excluir paciente [DELETE /api/v1/patients/{id}]
    + Request (application/json)

        + Headers

                SECRET_TOKEN: [TOKEN]

    + Response 200 (application/json)
        + Body

               {
                   "success": "patient deleted"
               }
    + Response 400 (application/json)
        + Body

               {
                   "code": 400,
                   "status": "error",
                   "message": "invalid id provided",
                   "time_stamp": "2022-12-07 14:55:13"
               }
    + Response 404 (application/json)
        + Body

               {
                   "code": 400,
                   "status": "error",
                   "message": "an error occurred while trying to delete patient, please check if a patient with ID provided exist or he has not/held appointments",
                   "time_stamp": "2022-12-07 14:55:13"
               }

 * ### Marcação de consulta:
   Deve ser possível atribuir a um **paciente** uma consulta com um **dentista** em uma determinada **data e hora**, e também adicionar uma **descrição** à consulta. Solicita-se o desenvolvimento de um _CRUD_ para a entidade **Consulta**.
   
   #### Métodos
   Requisições para a API devem seguir os padrões:

   | Método   | Descrição                                                                                                                |
   |----------|--------------------------------------------------------------------------------------------------------------------------|
   | `POST`   | Adicionar consulta                                                                                                       |
   | `GET`    | Trazer consulta pelo ID                                                                                                  |
   | `PUT`    | Atualizar consulta                                                                                                       |
   | `PATCH`  | Atualizar uma consulta por algum dos seus campos                                                                         |
   | `DELETE` | Excluir consulta.                                                                                                        |
   | `POST`   | Adicionar consulta pelo RG do paciente e matrícula do dentista.                                                          |
   | `GET`    | Trazer consulta pelo RG do paciente. Deve conter o detalhamento da consulsta (Data-Hora, descrição, Paciente e Dentista) |

## Requerimentos técnicos
A aplicação deve ser desenvolvida em design orientado a pacotes:
* **Camada/domínio** de entidades de negócio
* **Camada/domínio** de acesso a dados (Repository)
* **Camada de acesso a dados (banco de dados)**: é o banco de dados do nosso sistema. Você poderá usar qualquer um dos bancos de dados relacionais modelado através de um modelo
entidade-relação, como H2 ou MySQL, ou não relacional, como o Mongo DB.
* **Camada/domínio** service
* **Camada/domínio** handler