## Project Overview

This project provides a user-friendly interface for traders to manage their real-time trading records. It is built with `React18`,`UmiJs`, `ahooks`, `TypeScript`, `socket.io`, `Ant Design`, and `Styled-Component` on the frontend, and `NodeJs`, `Nestjs`, `typeorm`, `sqlite3`, and `websockets` on the backend.

## Getting Started

1. Install `Yarn` if you don't have it installed by following the instructions [here](https://yarnpkg.com/getting-started/install).

1. Go to the root directory of the project and run `yarn` to install dependencies.
1. Start the web application by running `yarn start:dev` or `yarn start:test`.
1. Open your browser and go to http://localhost:8000 to view the application.
1. To start the server, go to the `server/` directory and `run yarn && yarn start`. The service defaults to port `3000`.
1. To build the project, run `yarn build` in the root directory. The compiled static files will be placed in the `server/web/` directory.
1. Login: UserName `admin`, Password `admin`.
1. Unit test: `yarn test`

If you just want to see the effect and don't want to start the front-end project, you can directly start the `server` project, and then open `http://localhost:3000/` to see the same effect as above.

<img src="https://github.com/stupidWall/trading-data-manage/blob/main/screenshots/demo.gif?raw=true" />

### Project Structure

The project has a directory structure generated by the `umijs` -[documentation](https://umijs.org/docs/guides/directory-structure), and the frontend code is located in the root directory, while the backend code is located in the `server` directory.

### Technology Stack

The project uses the latest technologies to ensure efficient performance and high code quality.

- `Why Umijs`:
  - Umi provides built-in routing, construction, deployment, and testing, it can meet 80% of daily development needs
- `Why ahooks`:
  - Reduce the amount of code, improve code reuse
  - Speed up development
- `Why Styled-Component`:

  - CSS is tied to component logic, modular, and easier to maintain
  - Separate CSS scope to prevent style conflicts

- `Why Nestjs`:
  - TypeScript support
  - Modular design, especially friendly for developers who have learned Angular
  - Clearer code and easier to maintain
  - Efficient performance
- `Why Typeorm + Sqlite3`
  - Typeorm: Easily operate the database; multiple data source support, like `PostgreSQL`, `MySQL`,`SQLite`
  - Sqlite3: Simple to use; Very high performance and can handle large amounts of data;

### Code Quality

The project follows best practices for code quality, including using `@umijs/fabric` + `eslint`, `lint-staged` + `Husky`, `Prettier`, and following the [Git Flow](https://nvie.com/posts/a-successful-git-branching-model/) branching model.

### Performance Optimization

- To address the requirement of displaying more than `10,000` records in a table, `virtualized` table technique is used to optimize performance
- React component rendering performance is optimized using `React.memo`
- Data is cached using `useMemo` to improve performance
- Function performance is optimized using `useCallback`
- Render timing is optimized using `requestAnimationFrame`
- To ensure accurate update order in situations where each row of the table may experience large number of updates in a short time, a queueing mechanism is used.
- To handle the frequent data updates from the server, a throttle mechanism with a `50` millisecond interval has been implemented to reduce the frequency of data pushes. This mechanism stores all data updates within the `50` millisecond interval in a queue data structure, then pushes them to the front-end in a batch, reducing the rendering pressure on the front-end.

### Question

- Can we use `canvas` instead of `virtual list`, will it perform better? If so, how? (follow up research)
- In the face of performance problems caused by high-frequency triggering of high-frequency re-rendering, is there any other better optimization solution? Or is there a more profitable optimization direction?
- In the face of frequent update events, how can the backend better ensure the atomicity of data, and can message queues be used for optimization?
- The backend stores data, can it be combined with `redis` to improve the response speed, if so, how to do it?
